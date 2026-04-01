# Example: Map Figure from a Stata-Processed `.dta` File

This example shows how to build a **publication-ready map figure in R** after `Stata` has already processed the analytical data and exported a plotting-ready `.dta` file.

This example is especially suitable for empirical economics and agricultural economics papers that need to show:

- regional descriptive patterns
- provincial or county-level variation
- geographic distribution of outcomes, treatments, or indices
- spatial heterogeneity in descriptive evidence

The workflow follows the default logic of this repository:

- `Stata` handles data cleaning, sample construction, aggregation, and exports a processed `.dta`
- `R` handles map production, styling, annotation, panel composition, and export

---

## Figure Purpose

This figure is designed to help the reader see:

- the geographic distribution of a key variable
- which regions are relatively high or low
- whether there are visible regional clusters or gradients
- how the descriptive spatial pattern supports the broader empirical narrative

A map should be used only when geography itself is analytically meaningful.  
It should not be used as decoration.

---

## Typical Use Case

This type of figure is appropriate when the paper needs to show:

- provincial averages of dietary quality
- county-level environmental indicators
- regional distribution of adoption, expenditure, or productivity
- spatial descriptive patterns before formal econometric analysis
- geographic heterogeneity that motivates later subgroup or spatial analysis

Typical manuscript placement:

- **main text** if the map conveys a central descriptive fact
- **appendix** if it is mainly supportive or supplementary

---

## Expected Input Data

The recommended workflow is that `Stata` exports a `.dta` file containing the map key and the variable to be plotted.

A typical processed `.dta` may contain:

| variable | meaning |
|---|---|
| `province_name` | province name used for merging with the shapefile |
| `province_code` | province code if needed |
| `value` | the variable to be mapped |
| `year` | year if one specific year is plotted |
| `group_label` | optional group or panel label |

At minimum, the plotting dataset should contain:

- one geographic merge key
- one mapped variable

If the map is for one cross-section, the `.dta` should already be filtered to the relevant year in `Stata`.

---

## Recommended Stata Output Logic

The preferred workflow is:

1. clean and aggregate the data in `Stata`
2. keep only the geographic identifiers and mapped variable
3. save the figure-ready dataset as `.dta`
4. let `R` merge that `.dta` with the shapefile and produce the final map

A stylized Stata workflow might look like:

```stata
* Example idea only
use "analysis_data/main_panel.dta", clear

keep if year == 2015
collapse (mean) value = chei_score, by(province_name)

save "data/figure_data/map_chei_2015.dta", replace
```

In a real project, the variable name and aggregation rule should match the substantive figure goal.

---

## Complete R Example

```r
# ==========================================================
# Example: Publication-ready provincial map from Stata .dta
# ==========================================================

# -------------------------
# 0. Packages
# -------------------------
library(tidyverse)
library(sf)
library(haven)
library(showtext)
library(ggspatial)
library(ggnewscale)
library(RColorBrewer)

# -------------------------
# 1. Fonts
# -------------------------
# Adjust these font paths to your own system if needed
font_add("Arial", 
         regular = "/System/Library/Fonts/Supplemental/Arial.ttf",
         italic = "/System/Library/Fonts/Supplemental/Arial Italic.ttf",
         bold = "/System/Library/Fonts/Supplemental/Arial Bold.ttf")

showtext_auto()
plot_font <- "Arial"
# -------------------------
# 2. Read shapefiles
# -------------------------
# Example
etwd("/Users/xuanzhichong/Documents/R语言/使用 R 语言绘制填充地图、栅格地图 + 等降水量线")

provmap <- read_sf("chinaprov2019mini/chinaprov2019mini.shp") %>%
  filter(!is.na(省代码))

provlinemap <- read_sf("chinaprov2019mini/chinaprov2019mini_line.shp") %>%
  filter(class %in% c("九段线", "海岸线", "小地图框格")) %>%
  select(class)

# -------------------------
# 3. Read Stata-processed .dta
# -------------------------
map_df <- read_dta("data/figure_data/map_chei_2015.dta") %>%
  mutate(
    province_name = as.character(province_name)
  )

# -------------------------
# 4. Merge map and data
# -------------------------
provmap_plot <- provmap %>%
  left_join(map_df, by = c("省" = "province_name"))

# -------------------------
# 5. Build a restrained Nature-style theme
# -------------------------
theme_map_nature <- function() {
  theme_minimal(base_family = plot_font) +
    theme(
      axis.text = element_blank(),
      axis.title = element_blank(),
      panel.grid = element_blank(),
      legend.position = c(0.88, 0.30),
      legend.justification = c("center", "bottom"),
      legend.title = element_text(size = 11, face = "bold"),
      legend.text = element_text(size = 9, colour = "black"),
      plot.title = element_text(size = 13, face = "bold", hjust = 0.5),
      plot.subtitle = element_text(size = 10, hjust = 0.5),
      plot.caption = element_text(size = 8.5, hjust = 0),
      plot.tag = element_text(size = 13, face = "bold"),
      plot.tag.position = "topleft",
      plot.background = element_rect(fill = "white", colour = NA),
      panel.background = element_rect(fill = "white", colour = NA)
    )
}

# -------------------------
# 6. Plot
# -------------------------
p_map <- ggplot(data = provmap_plot) +
  geom_sf(
    aes(fill = value),
    color = "grey92",
    linewidth = 0.18
  ) +
  geom_sf(
    data = provlinemap,
    color = "grey65",
    linewidth = 0.28
  ) +
  scale_fill_gradientn(
    name = "CHEI",
    colors = c("#86B5D3", "#FBFBF6", "#E38A8A"),
    na.value = "#D6D7D6",
    guide = guide_colorbar(
      title.position = "top",
      title.hjust = 0.5,
      barwidth = unit(0.55, "cm"),
      barheight = unit(4.6, "cm")
    )
  ) +
  annotation_north_arrow(
    location = "bl",
    which_north = "grid",
    pad_x = unit(0.9, "in"),
    pad_y = unit(0.35, "in"),
    height = unit(0.9, "cm"),
    width = unit(0.9, "cm"),
    style = north_arrow_minimal
  ) +
  annotation_scale(
    location = "bl",
    width_hint = 0.28,
    text_family = plot_font
  ) +
  labs(
    title = "Dietary Quality of Chinese Rural Residents in 2015",
    subtitle = "Provincial average CHEI scores",
    caption = "Notes: The map reports province-level average values from the Stata-processed analytical dataset. Grey areas indicate missing values.",
    tag = "a"
  ) +
  theme_map_nature()

# -------------------------
# 7. Export
# -------------------------
ggsave(
  filename = "output/figures/fig1_map_chei_2015.pdf",
  plot = p_map,
  width = 7.2,
  height = 5.8,
  units = "in",
  dpi = 600
)
```

---

## Why This Example Works

This example follows the recommended workflow of the repository.

### 1. `Stata` remains the analytical backend
The aggregation, sample selection, and construction of the mapped variable happen in `Stata`, not in `R`.

### 2. `R` focuses on cartographic presentation
`R` handles:

- reading the processed `.dta`
- merging with the shapefile
- map styling
- legend control
- north arrow and scale bar
- export

### 3. The map remains analytically disciplined
The figure shows one substantive spatial pattern clearly rather than trying to display too many dimensions at once.

### 4. The visual design is restrained
The map uses:

- soft province borders
- subtle line layers
- a restrained gradient
- compact legend placement
- minimal annotation
- strong readability in grayscale and print settings

---

## Nature-Style Design Choices in This Example

This example uses a restrained style consistent with Nature-like visual expectations:

- clean white background
- minimal clutter
- carefully controlled legend
- muted geographic boundaries
- restrained gradient rather than loud categorical colors
- compact but readable title hierarchy
- elegant map furniture kept secondary to the analytical content

This is preferable to:

- overly saturated choropleth colors
- thick black province borders
- large decorative north arrows
- oversized legends
- too many text labels crowding the map

---

## Suggested Caption

A manuscript-ready caption could be written as:

> **Figure X. Provincial distribution of dietary quality in rural China, 2015.**  
> The map reports province-level average China Healthy Eating Index (CHEI) scores constructed from the analytical dataset. Darker shades indicate higher average dietary quality. Grey areas indicate missing values. The figure is descriptive and is intended to summarize spatial variation before the regression analysis.

If the figure is for another variable, revise accordingly:

> **Figure X. Provincial distribution of [variable], [year].**  
> The map reports province-level average values from the Stata-processed analytical dataset. The figure is descriptive and summarizes cross-regional variation in [variable].

---

## Suggested Manuscript Language

Useful prose around the figure could be:

- `Figure X shows the provincial distribution of dietary quality in 2015.`
- `A clear geographic gradient is visible, with relatively higher values concentrated in ...`
- `The map is descriptive, but it helps illustrate the substantial regional variation underlying the later analysis.`
- `This spatial pattern motivates the heterogeneity analysis reported in Section X.`

If caution is needed:

- `The figure should be interpreted as descriptive rather than causal evidence.`
- `The map summarizes cross-regional variation but does not by itself identify the sources of that variation.`

---

## Common Mistakes to Avoid

Do not:

- map variables that have no meaningful geographic interpretation
- overload one map with too many annotations
- use overly saturated colors
- use a color scale that hides meaningful gradients
- omit a clear note about missing values
- mix province names that do not match the shapefile merge key
- let the map imply causal interpretation when it is only descriptive
- use decorative cartographic elements that distract from the data

---

## When This Figure Belongs in the Main Text

Prefer main-text placement when the map:

- shows a central descriptive spatial fact
- motivates later heterogeneity or spatial analysis
- helps the reader understand the empirical setting
- provides meaningful context that a table cannot convey as clearly

---

## When This Figure Belongs in the Appendix

Prefer appendix placement when the map:

- is only supplementary
- repeats information already conveyed clearly elsewhere
- shows an alternative descriptive cut that is not central to the narrative
- provides transparency but not a main analytical message

---

## Working Rule

A good map figure should let the reader answer quickly:

1. what variable is being mapped?
2. at what geographic level?
3. for what year or sample?
4. where are values relatively high or low?
5. why is geography analytically relevant here?
6. is the map descriptive rather than over-interpreted?

If the map is visually attractive but does not improve substantive understanding, it probably does not belong in the main paper.

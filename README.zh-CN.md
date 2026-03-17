# Econ Scholar Workflow for Codex

杩欐槸涓€涓潰鍚?`瀹炶瘉寰 / 鏀跨瓥璇勪及` 鐨?Codex 宸ヤ綔娴佽鍐欏眰锛岄粯璁ゆ湇鍔′簬锛?
- 瀹炶瘉寰缁忔祹瀛?- 鏀跨瓥璇勪及
- `Stata + Python`
- 璁烘枃鍐欎綔銆佹姇绋垮墠 QA銆乣R&R` 鍥炲

杩欎釜浠撳簱涓嶆槸鐙珛绋嬪簭锛岃€屾槸涓€濂楀伐浣滄祦閰嶇疆鍖咃紝涓昏鐢辫繖浜涢儴鍒嗙粍鎴愶細

- `AGENTS.md`锛氶」鐩骇璺敱鍜屽伐浣滄祦瑙勫垯
- `agents/`锛氫笓闂?agent 鐨勬彁绀鸿瘝
- `skills/`锛氬彲澶嶇敤宸ヤ綔娴佽鏄?- `config.example.toml`锛欳odex 閰嶇疆绀轰緥
- `quality_reports/`锛歈A 鎶ュ憡妯℃澘鍜岃緭鍑虹洰褰?
## 杩欏宸ヤ綔娴侀粯璁ゆ€庝箞鐞嗚В浣犵殑浠诲姟

鍦ㄨ繖涓粨搴撻噷锛孋odex 榛樿鎸夌粡娴庡瀹炶瘉璇鐞嗚В浣犵殑璇锋眰锛?
- 鈥滅粨鏋溾€濋粯璁ゆ槸鍥炲綊琛紝涓嶆槸 benchmark leaderboard
- 鈥滃疄楠屸€濋粯璁ゆ槸瀹炶瘉璁捐锛屼笉鏄ā鍨嬭缁?- 鈥滆鏂団€濋粯璁ゆ槸缁忔祹瀛﹁鏂囩粨鏋勶紝涓嶆槸 AI conference 缁撴瀯
- 鈥滃绋垮洖澶嶁€濋粯璁ゆ槸鏈熷垔 `R&R`锛屼笉鏄?conference rebuttal

榛樿鏍堟槸锛?
- 鏂囩尞锛歚Google Scholar`銆乣RePEc`銆乣IDEAS`銆乣NBER`銆乣AEA journals`
- 鍒嗘瀽锛歚Stata` 涓轰富锛宍Python` 鍋氳緟鍔?- 浜х墿锛歚literature-review.md`銆乣analysis-plan.md`銆乣regression-spec-matrix.md`銆乣response-letter.md`

## 蹇€熷紑濮?
### 1. 鎶婅繖涓粨搴撳綋鎴愬伐浣滄祦瑕嗗啓灞?
杩欎笉鏄€滅洿鎺ヨ繍琛屸€濈殑浠撳簱锛岃€屾槸鐢ㄦ潵鍚堝苟杩涗綘鑷繁鐨?Codex 鐜銆?
鍏抽敭鏂囦欢锛?
- `AGENTS.md`锛氶」鐩骇璺敱鍜岃涓虹害鏉?- `config.example.toml`锛歛gent銆乫eature銆丮CP 鐨勯厤缃ず渚?- `agents/`锛氫笓闂?agent 鐨勭郴缁熸彁绀?- `skills/`锛氭湰鍦?workflow 璇存槑

### 2. 閰嶇疆 Codex

鎶?`config.example.toml` 褰撴垚鍙傝€冩ā鏉匡紝鐢ㄦ潵鍚堝苟杩欎簺鍐呭锛?
- 寮€鍚?`multi_agent`
- 寮€鍚?`memories`
- 寮€鍚?`skill_approval`
- 娉ㄥ唽 economics agents
- 鍚敤 Zotero MCP

娉ㄦ剰锛?
- 褰撳墠浠撳簱閲岀殑 `config.example.toml` 浠嶇劧淇濈暀浜?model/provider 鐨勫崰浣嶇
- 浣犲簲褰撴妸鐮旂┒宸ヤ綔娴佺浉鍏崇墖娈靛悎骞跺埌鐪熷疄鐨?`~/.codex/config.toml`
- 涓嶈鎶?`your-api-key` 杩欑被鍗犱綅绗﹀師鏍锋斁杩涙寮忛厤缃?
### 3. 鍙€変絾寮虹儓鎺ㄨ崘锛氶厤缃?Zotero MCP

濡傛灉浣犳兂鐩存帴浣跨敤鏂囩尞瀵煎叆銆乧ollection 绠＄悊鍜?PDF 鑾峰彇鑳藉姏锛岄厤缃?Zotero MCP銆?
鍙傝€冿細

- `MCP_SETUP.md`
- `MCP_SETUP.zh-CN.md`

### 4. 鍦ㄩ」鐩牴鐩綍鍚姩 Codex

杩欐牱 Codex 鎵嶄細鑷姩璇诲彇椤圭洰绾?`AGENTS.md`銆?
寤鸿绗竴娆′細璇濈洿鎺ヨ繖鏍疯锛?
```text
璇诲彇 AGENTS.md锛屾妸杩欎釜浠撳簱褰撴垚缁忔祹瀛﹀疄璇佸伐浣滄祦銆傛垜鐜板湪鍦ㄥ仛 [topic]锛岃鏍规嵁褰撳墠闃舵甯垜杩涘叆姝ｇ‘ workflow銆?```

## 鍙敤宸ヤ綔娴?
### 闃舵 1锛氱爺绌舵瀯鎬濅笌鏂囩尞缁艰堪

浣跨敤锛?
- `research-ideation`
- `literature-reviewer`

杈撳嚭锛?
- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `research-design.md`

閫傚悎锛?
- 鏀剁獎鐮旂┒闂
- 姊崇悊璇嗗埆绛栫暐
- 鍒ゆ柇鏂囩尞鏄惁宸茬粡楗卞拰
- 璇勪及鏁版嵁鏄惁鍙緱

### 闃舵 2锛氭暟鎹璁′笌鍒嗘瀽瑙勫垝

浣跨敤锛?
- `results-analysis`
- `data-analyst`

杈撳叆锛?
- `.dta`
- `.do`
- `.log`
- `.csv`
- `.xlsx`
- 鍥炲綊琛?`.tex`

杈撳嚭锛?
- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`

閫傚悎锛?
- 杩樺師 do-file 鎵ц椤哄簭
- 璁板綍鏍锋湰鏋勯€?- 瑙勫垝涓诲洖褰?- 璁捐绋冲仴鎬у拰闄勫綍琛?
### 闃舵 3锛氳鏂囧啓浣?
浣跨敤锛?
- `ml-paper-writing`
- `paper-miner`

榛樿缁撴瀯锛?
1. `Introduction`
2. `Institutional background / context`
3. `Data`
4. `Empirical strategy / identification`
5. `Main results`
6. `Mechanisms / heterogeneity`
7. `Robustness`
8. `Conclusion`
9. `Appendix`

缁忔祹瀛︽ā鏉垮叆鍙ｏ細

- `skills/ml-paper-writing/templates/econ/README.md`

### 闃舵 4锛氭姇绋垮墠 QA

浣跨敤锛?
- `paper-self-review`锛氶潤鎬佽嚜瀹?- `qa-paper`锛氫弗鏍?critic/fixer/verifier 闂幆

褰撲綘闇€瑕佽繖浜涜兘鍔涙椂锛屼紭鍏堢敤 `qa-paper`锛?
- 鏄庣‘鐨?go / no-go 鍒ゆ柇
- 鎵撳垎
- 澶氳疆 review-fix
- 鎻愪氦鍓?hard gates

### 闃舵 5锛歊&R 涓庡绋垮洖澶?
浣跨敤锛?
- `review-response`
- `rebuttal-writer`
- `qa-response`

榛樿杈撳嚭锛?
- `response-letter.md`
- `comment-to-change-map.md`

## 绗簩杞?QA 绯荤粺

杩欎釜浠撳簱宸茬粡闆嗘垚浜?Codex 鍘熺敓鐨?`critic/fixer` 妯″紡銆?
### Agents

- `paper-critic`
- `paper-fixer`
- `response-critic`
- `response-fixer`
- `artifact-verifier`

### Skills

- `qa-paper`
- `qa-response`

### 寰幆

```text
pre-flight -> critic -> fixer -> verifier -> 蹇呰鏃剁户缁?-> APPROVED 鎴栨渶澶?5 杞?```

### 闃堝€?
- `80` = commit-ready
- `90` = submission-ready
- `95` = excellence

### Hard Gates

璁烘枃锛?
- 璇嗗埆閫昏緫閿欒
- 鍏抽敭鏂囧瓧涓庤〃鏍间笉涓€鑷?- 寮曠敤涓嶅彲鏍搁獙鎴栧け鐪?- 缂哄皯鍩烘湰澶嶇幇璇存槑

Response锛?
- 婕忓洖鍏抽敭 referee 鎰忚
- 鎵胯淇敼浣嗘棤娉曡拷韪?- response 涓?change map 涓嶄竴鑷?- 璇皵鏄庢樉鍥為伩鎴栬瀵?
鎶ュ憡浼氬啓鍏ワ細

- `quality_reports/papers/`
- `quality_reports/responses/`
- `quality_reports/verifier/`

## 瀹炵敤鎻愮ず璇?
### 浠庢枃鐚患杩板紑濮?
```text
鎴戞兂鐮旂┒ [topic]銆傝浣跨敤缁忔祹瀛﹀疄璇佸伐浣滄祦锛屽厛甯垜鍋氭枃鐚湴鍥俱€佽瘑鍒瓥鐣ユ⒊鐞嗗拰鍙敤鏁版嵁璇勪及銆?```

### 瀹¤涓€涓?Stata 椤圭洰

```text
鎴戞湁涓€濂?do-file 鍜?dta銆傝杩樺師鏁版嵁娴佺▼銆佽瘑鍒?estimation sample锛屽苟鐢熸垚 regression-spec matrix銆?```

### 鍐?Main Results

```text
璇锋牴鎹繖浜涘洖褰掔粨鏋滐紝鐢?economics journal 椋庢牸璧疯崏 Main Results 鍜?Empirical Strategy銆?```

### 璺戜弗鏍艰鏂?QA

```text
瀵硅繖涓?draft 杩愯 qa-paper銆傛垜闇€瑕?hard gates銆佹墦鍒嗗拰鏄庣‘鐨?submission-readiness 缁撹銆?```

### 鍐欏苟瀹℃煡 R&R 鍥炲

```text
鍏堢敤 review-response 璧疯崏 response letter锛屽啀鐢?qa-response 鍋氭渶缁?QA銆?```

## 浠撳簱缁撴瀯

- `AGENTS.md`锛氶」鐩骇璺敱鍜岃川閲忚鍒?- `config.example.toml`锛欳odex 閰嶇疆绀轰緥
- `agents/`锛氫笓闂?reviewer / worker 鎻愮ず璇?- `skills/`锛氬伐浣滄祦璇存槑鍜屽弬鑰冭祫鏂?- `quality_reports/`锛歈A 鎶ュ憡鐩綍鍜屾ā鏉?

## 褰撳墠鑼冨洿

褰撳墠宸茬粡瑕嗙洊寰楁瘮杈冨ソ鐨勯儴鍒嗭細

- 瀹炶瘉寰
- 鏀跨瓥璇勪及
- `Stata + Python`
- 璁烘枃鍜?`R&R` 鐨?QA 闂幆

褰撳墠杩樻病鏈夊仛娣辩殑閮ㄥ垎锛?
- 澶嶇幇鍖呯殑娣卞害瀹¤
- 鏁版嵁娓呯悊 QA 鐨勭嫭绔?critic/fixer
- 鐞嗚缁忔祹瀛﹀伐浣滄祦




# Pseudo-Structure-Detection-Model-v0.1
Draft defensive detection model for Immune Royalty OS, distinguishing pseudo-structures from independent emergence through path, transformation, context, and boundary-aware scoring.

擬似構造検出の初期仕様

Pseudo Structure Detection Model v0.1（PSDM v0.1） は、
Immune Royalty OS v0.1 における防御実装レイヤーの中核モデルです。

この仕様の目的は、
独立到達や同期的収束を誤爆せずに、経路の短い擬似的新規構造のみを高精度で検出し、reject / hold / audit を安全に分離すること にあります。

ここで重要なのは、
このモデルが 「似ているものを落とす装置」ではない という点です。
本仕様が目指すのは、独立創造を守りながら、擬似的新規だけを狭く正確に落とすこと です。

1. なぜ擬似構造検出が必要なのか

印税OSや免疫型の価値循環システムでは、
痕跡を守るだけでは足りません。
その保護構造を逆手に取った、擬似的新規 を見分ける必要があります。

たとえば、

既存構造に極端に近い
経路が短い
実質的変容が薄い
文脈差が乏しい
それにもかかわらず新規構造のように振る舞う

といったケースです。

しかし、この検出は危険でもあります。
厳しすぎる判定は、

独立到達
シンクロニシティ
十分な変容を伴う派生
異なる文脈での再構成

まで誤って落としてしまうからです。

PSDM v0.1 は、この危険を避けるために、
類似だけで切らず、経路・変容・文脈・境界安全性を組み合わせて判定する モデルとして設計されています。

2. このモデルの目的

PSDM v0.1 は、次の5つを主目的とします。

擬似構造の最小定義を明確化する
類似のみを理由とした誤排除を防ぐ
Path・Transformation・Context を併用して判定する
Boundary 混乱時は自動 reject を避ける
explainable な reject / hold / audit 出力を生成する

つまりこのモデルは、
排除のための乱暴なフィルター ではなく、
誤爆を抑えた狭い防御刃 です。

3. 設計原理

PSDM v0.1 は、以下の5原理に基づいて設計されます。

3.1 Similarity is not Enough

類似度単独では擬似構造とみなさない。
高い類似性は、あくまで警戒信号のひとつに過ぎない。

3.2 Protect Independent Arrival

独立到達や同期的収束を先に救う。
防御より先に、保護すべきものを見分ける。

3.3 Reject is Narrow

自動 reject の条件は狭く厳格にする。
落とすより、まず hold / audit に送る。

3.4 Boundary before Ban

自己／非自己境界が曖昧な場合は、reject より hold / audit を優先する。

3.5 Explainable Defense

排除・保留・監査の理由は、常に説明可能でなければならない。

4. 擬似構造の定義

PSDM v0.1 では、擬似構造を次のように定義します。

擬似構造とは、既存痕跡への依存が強く、生成経路が短く、実質的変容が薄く、文脈独立性が乏しいため、新規構造として保護する根拠が弱い構造である。

ここで重要なのは、
高い類似度だけでは擬似構造とはいえない という点です。

擬似構造ではない例
独立した経路から偶然収束した構造
十分な変容を伴う派生構造
文脈と目的が大きく異なる再構成
5. このモデルが使う変数

PSDM v0.1 では、最低限以下の変数を用います。

コア変数
S: Similarity Score

構造類似度。
どれだけ既存構造に近いかを表します。

P: Path Independence Score

生成経路の独立性。
どれだけ独立した道筋で到達したかを表します。

T: Transformation Score

実質的変容量。
親構造からどれだけ本質的に変化したかを表します。

Cx: Context Divergence Score

文脈差分。
用途・目的・周辺文脈がどれだけ異なるかを表します。

L: Path Length Score

経路の長さ、または経路の豊かさ。
生成に十分な中間過程があるかを見ます。

免疫補助変数
B: Boundary Confusion Score

自己／非自己境界の混乱度。
高いほど、作者性や親子関係の誤認リスクが高い。

I: Inflammation Score

過敏反応リスク。
高いほど、システムが炎症状態にある。

Z_tol: Tolerance Score

Tolerance Zone で計算された寛容スコア。
高いほど、擬似構造判定から保護されやすい。

依存補助変数
D_ref: Direct Reference Dependency

既存痕跡への直接依存度。

Mx: Mutation Density

局所的変異密度。
表面的な書き換えではなく、変異の厚みがあるかを見る補助指標です。

6. 危険信号と保護信号

PSDM v0.1 では、擬似構造らしさと保護価値を分けて見ます。

擬似構造の危険信号
S が高い
P が低い
T が低い
Cx が低い
L が低い
D_ref が高い
Mx が低い
保護すべき信号
P が高い
T が高い
Cx が高い
L が豊か
Z_tol が高い
直接依存が弱い
7. 擬似構造リスクの基本式
7.1 基本リスク

まず、擬似構造リスク R_pseudo を計算します。

R_pseudo = (0.30 * S) + (0.25 * (1 - P)) + (0.20 * (1 - T)) + (0.15 * (1 - Cx)) + (0.10 * (1 - L))

これは、

似ているほど高い
経路独立性が低いほど高い
変容が薄いほど高い
文脈差が小さいほど高い
経路が短いほど高い

というリスク合成式です。

7.2 依存ペナルティ

次に、直接依存と変異不足を補助的に加算します。

P_dep = (0.70 * D_ref) + (0.30 * (1 - Mx))
7.3 寛容文脈を加味した最終リスク

Tolerance Zone の結果も踏まえて、最終擬似構造リスク R_adj を計算します。

R_adj = clamp(R_pseudo + (0.20 * P_dep) - (0.15 * max(0, Z_tol)), 0, 1)

つまり、

依存が強ければリスクを上げる
寛容スコアが高ければリスクを下げる

という形です。

7.4 擬似構造確信度

さらに、境界混乱と炎症状態を差し引いた確信度 C_pseudo を計算します。

C_pseudo = (0.50 * R_adj) + (0.25 * (1 - B)) + (0.25 * (1 - I))

高リスクでも、
境界が曖昧 または 炎症状態 なら、確信度は下がります。

8. 初期閾値

PSDM v0.1 では、次の初期閾値を置きます。

candidate_threshold = 0.62
hard_reject_threshold = 0.78
audit_threshold = 0.68
path_independence_max_for_reject = 0.35
transformation_max_for_reject = 0.25
context_divergence_max_for_reject = 0.30
boundary_hold_trigger = 0.50
inflammation_hold_trigger = 0.65
dependency_penalty_trigger = 0.60
tolerance_protection_floor = 0.40

これらは v0.1 の初期値であり、
将来的には事例ベースで調整されます。

9. 判定クラス

PSDM v0.1 では、候補を次の6種類に分類します。

independent_arrival

独立経路による到達。擬似構造ではない。

tolerated_derivation

派生だが十分な変容があり、許容される。

pseudo_candidate

擬似構造の候補。

hard_pseudo_structure

自動 reject 可能な擬似構造。

boundary_uncertain

境界が曖昧で、保留が必要。

audit_required

高リスクだが不確実性も大きく、監査が必要。

10. 評価パイプライン

PSDM v0.1 は、次の順で判定を行います。

Step 1

Boundary check
B >= boundary_hold_trigger または I >= inflammation_hold_trigger なら、まず hold / audit へ送る。

Step 2

Tolerance protection check
Z_tol >= tolerance_protection_floor なら、自動 reject から除外する。

Step 3

R_pseudo を計算する。

Step 4

P_dep を計算する。

Step 5

R_adj を計算する。

Step 6

C_pseudo を計算する。

Step 7

pseudo candidate を割り当てる。

Step 8

厳格 reject 条件を満たすか確認する。

Step 9

曖昧なものを audit に振り分ける。

11. 優先順位ルール

PSDM v0.1 では、次の優先順位を取ります。

Rule 1

B >= 0.50
→ hold_for_boundary_review

境界混乱時は、自動 reject を禁止します。

Rule 2

I >= 0.65
→ hold_due_to_inflammation

炎症時は誤排除が増えやすいため、先に止めます。

Rule 3

Z_tol >= 0.40
→ protect_from_auto_reject

寛容保護帯に入っている構造は先に救います。

Rule 4

R_adj >= 0.62
→ classify_as_pseudo_candidate

擬似構造候補として審査対象に入れます。

Rule 5

R_adj >= 0.78 AND P < 0.35 AND T < 0.25 AND Cx < 0.30 AND B < 0.50
→ hard_reject

この厳格条件を満たした場合のみ、自動 reject が可能です。

Rule 6

R_adj >= 0.68 AND (B >= 0.35 OR I >= 0.40)
→ audit_required

高リスクだが不確実性が残るため、監査に送ります。

12. 自動 reject の考え方

このモデルで最も重要なのは、
自動 reject の条件を狭く取っていること です。

自動 reject 条件

以下を同時に満たす場合のみ、自動 reject 候補になります。

R_adj >= 0.78
AND P < 0.35
AND T < 0.25
AND Cx < 0.30
AND B < 0.50

つまり、

リスクが高い
経路独立性が低い
実質的変容が薄い
文脈差が小さい
しかも境界混乱が少ない

ときだけ落とす。

ここが狭いからこそ、
独立創造を守りやすい のです。

13. hold / audit / reject の分離

PSDM v0.1 では、これらを明確に分けます。

reject

明確に擬似構造と判定できるもの。

hold

境界混乱や炎症状態があり、追加レビューが必要なもの。

audit

高リスクだが影響が大きい、あるいは不確実性が大きく、人間判断が必要なもの。

つまりこのモデルは、
全自動BAN装置ではありません。
むしろ、reject を狭くし、hold / audit を広めに取る ことを重視しています。

14. 出力

PSDM v0.1 は、少なくとも以下を出力できるべきです。

主出力
R_pseudo
P_dep
R_adj
C_pseudo
final_classification
recommended_action
補助出力
triggered_precedence_rules
reject_condition_match
audit_condition_match
human_readable_reason
top_explanatory_factors
15. 説明テンプレート

本仕様では、判定理由を説明できなければなりません。

Reject

高い構造類似性、低い経路独立性、不十分な変容、最小限の文脈差、低い境界曖昧性を理由に、擬似構造として reject する。

Hold

擬似構造リスクは高いが、境界混乱や炎症状態があり、安全な自動 reject ができないため保留する。

Audit

擬似構造リスクは高いが、不確実性が残るため人間監査に送る。

Protect

寛容シグナル、経路独立性、変容強度のいずれかが十分であるため、擬似構造 reject から保護する。

16. 典型例
例1：独立収束
S = 0.84
P = 0.81
T = 0.46
Cx = 0.58
Z_tol = 0.57

この場合、類似度は高くても独立性と変容が十分あるため、
independent_arrival / protect に分類されます。

例2：派生だが許容
S = 0.78
P = 0.54
T = 0.42
Cx = 0.44
Z_tol = 0.43

この場合、派生ではあるが十分な変容と文脈差があるため、
tolerated_derivation / tolerate に入ります。

例3：明確な擬似構造
S = 0.94
P = 0.18
T = 0.11
Cx = 0.14
B = 0.16

この場合、短経路・低変容・低文脈差・低境界混乱が揃っているため、
hard_pseudo_structure / reject に入ります。

例4：高リスクだが境界曖昧
S = 0.91
P = 0.24
T = 0.19
Cx = 0.21
B = 0.57

この場合、高リスクでも境界混乱が高いため、
boundary_uncertain / hold になります。

例5：監査レベル
S = 0.89
P = 0.31
T = 0.24
Cx = 0.27
B = 0.39
I = 0.43

この場合、擬似構造リスクは高いが不確実性も残るため、
audit_required / audit になります。

17. ガバナンス
調整方針
human-supervised
レビュー周期
30日
監視指標
false_positive_rate
false_negative_rate
reject_precision
hold_to_reject_conversion_rate
audit_to_reject_conversion_rate
independent_arrival_misclassification_rate
調整対象
candidate_threshold
hard_reject_threshold
audit_threshold
path_independence_max_for_reject
transformation_max_for_reject
context_divergence_max_for_reject
boundary_hold_trigger
inflammation_hold_trigger
dependency_penalty_trigger
tolerance_protection_floor
禁止される挙動
類似度だけでの rejection
B が高い状態での自動 reject
Tolerance check を経ない reject
説明不能な reject
擬似構造検出を隠れた検閲として使うこと
18. 現時点の位置づけ

PSDM v0.1 は、
完成済みの全自動排除モデルではなく、最初の防御実装モデル です。

この段階で重要なのは、次の5点です。

類似度単独で切らない
独立到達を先に救う
reject 条件を狭くする
boundary / inflammation で hold / audit に逃がす
explainable な防御にする

つまり v0.1 は、
文明OSにおける擬似構造防御の最小骨格 です。

19. 今後の拡張候補
Domain-Specific Reject Profiles

分野ごとに reject 閾値や重みを切り替える。

Adaptive Context Divergence Modeling

文脈差分スコアを分野別・時系列別に適応調整する。

Multi-AI Pseudo Arbitration

複数AI間で擬似構造判定を裁定する。

Immune Map Binding

Immune Map 可視化レイヤーに reject / hold / audit 経路を接続する。

20. 一文で言えば

Pseudo Structure Detection Model v0.1 とは、
独立創造を誤爆せずに守りながら、
短経路・低変容・低文脈差の擬似的新規だけを狭く安全に検出するための防御実装モデルです。

## Repository Structure

This repository is organized as a specification-first model repository.

### Root files

- `README.md`  
  Main human-readable overview of the project, including conceptual framing, purpose, and usage guidance.

- `LICENSE`  
  Repository license information.

- `CHANGELOG.md`  
  Version history and notable changes across releases.

- `CITATION.cff`  
  Citation metadata for referencing this repository in academic, technical, or documentation contexts.

- `CONTRIBUTING.md`  
  Contribution guidelines for documentation, schema, examples, and validation workflow updates.

---

### Documentation

- `docs/one-page-spec.md`  
  Compact one-page specification for PSDM v0.1.  
  Intended for quick understanding, sharing, and lightweight reference.

---

### Model definition

- `yaml/`  
  YAML-based human-readable structured definition of the model.  
  This is the conceptual configuration layer of PSDM v0.1.

- `schema json/`  
  JSON Schema files used to define machine-valid structure and validation rules.

- `sample json/`  
  Example JSON payloads that are expected to validate against the schema.

---

### Automation

- `.github/workflows/validate-specs.yml`  
  GitHub Actions workflow that validates schema files and sample JSON automatically on push, pull request, or manual run.

---

### Design philosophy of the structure

The repository separates the project into four layers:

1. **Explanation layer**  
   Human-readable documents such as `README.md` and `docs/one-page-spec.md`

2. **Definition layer**  
   Structured model definitions in `yaml/`

3. **Validation layer**  
   Machine-checked schema definitions in `schema json/`

4. **Example layer**  
   Testable sample instances in `sample json/`

This separation helps keep the project readable for humans, testable by machines, and extensible across future versions.

# Qualtran Tutorial: 有限体 DLP 学習ロードマップ

Qualtran で有限体上の離散対数問題（DLP）の論理回路とリソースを見積もるための学習用 notebook 集です。

優先度は `◎◎ / ◎ / ○ / △ / ×` の順です。ディレクトリ番号は作成順であり、学習順は以下の索引に従ってください。

## セットアップ

```bash
uv sync
uv run jupyter lab
```

最初に [Setup and Sanity Check](notebooks/00_setup.ipynb) から公式ドキュメントを開きます。

## 推奨学習順

### 0. Fundamentals

まず [Fundamentals](notebooks/01_fundamentals/) を次の順で進めます。

1. [Bloqs Tutorial](notebooks/01_fundamentals/01_bloqs_tutorial.ipynb) ◎
2. [Data Types](notebooks/01_fundamentals/03_data_types.ipynb) ◎
3. [Protocols](notebooks/01_fundamentals/02_protocols.ipynb) ○
4. [Classical Simulation](notebooks/01_fundamentals/04_classical_simulation.ipynb) ◎
5. [Call Graph](notebooks/01_fundamentals/06_call_graph.ipynb) ◎
6. [Qubit Counts](notebooks/01_fundamentals/07_qubit_counts.ipynb) ◎
7. [Controlled](notebooks/01_fundamentals/09_controlled.ipynb) ◎
8. [Adjoint](notebooks/01_fundamentals/08_adjoint.ipynb) ○

[Tensor Simulation](notebooks/01_fundamentals/05_tensor_simulation.ipynb) は現段階では任意です。

### 1. Shor で Qualtran を一周する

- [Factoring and Shor's Algorithm](notebooks/04_bloqs_library/01_concepts/01_factoring_and_shor.ipynb) ◎
- [Factoring RSA](notebooks/04_bloqs_library/02_modular_arithmetic/01_factoring_rsa.ipynb) ○
- [Modular Multiplication / CModMulK](notebooks/04_bloqs_library/02_modular_arithmetic/02_modular_multiplication.ipynb) ○

### 2. Shor 型 DLP の上位構造

- [Textbook QFT](notebooks/04_bloqs_library/03_rotations/01_textbook_qft.ipynb) ○
- [Textbook Quantum Phase Estimation](notebooks/04_bloqs_library/03_rotations/02_textbook_qpe.ipynb) ◎
- [Elliptic Curve Cryptography](notebooks/04_bloqs_library/04_root_bloqs/01_elliptic_curve_cryptography.ipynb) ◎

ECC notebook は算術の詳細ではなく、`FindECCPrivateKey → ECPhaseEstimateR → ECAddR` という DLP の組み立て方を読むために使います。

### 3. 有限体 DLP の本命部分

次の順で [GF Arithmetic](notebooks/04_bloqs_library/05_gf_arithmetic/) を進めます。

1. [GF(2^m) Addition](notebooks/04_bloqs_library/05_gf_arithmetic/01_gf2_addition.ipynb) ◎
2. [GF(2^m) Add Constant](notebooks/04_bloqs_library/05_gf_arithmetic/02_gf2_add_constant.ipynb) ○
3. [GF(2^m) Multiplication](notebooks/04_bloqs_library/05_gf_arithmetic/03_gf2_multiplication.ipynb) ◎◎
4. [GF(2^m) Square](notebooks/04_bloqs_library/05_gf_arithmetic/04_gf2_square.ipynb) ○
5. [GF(2^m) Inverse](notebooks/04_bloqs_library/05_gf_arithmetic/05_gf2_inverse.ipynb) ○
6. [GF Polynomial Split / Join](notebooks/04_bloqs_library/06_gf_polynomials/01_gf_poly_split_join.ipynb) ○

Multiplication notebook では `GF2MulK` を最優先し、`GF2Multiplication`、shift、binary polynomial multiplication、Karatsuba を同じページで比較します。

### 4. 有限体 DLP baseline

[Finite-Field DLP Baseline](notebooks/05_dlp_baseline/01_finite_field_dlp_baseline.ipynb) を、自分の baseline 実装を書き始める場所として使います。

ここまで終えたら、一度 Qualtran の読み進めを止め、自分の問題設定へ baseline を移植します。

### 5. Baseline 後の最適化

最初に既存の Advanced Topics を使います。

- [Composite Bloq Manipulation](notebooks/03_advanced/01_composite_bloq_manipulation.ipynb) ◎
- [Specialized Controlled Implementations](notebooks/03_advanced/06_specialized_ctrl.ipynb) ◎
- [T Complexity](notebooks/03_advanced/03_t_complexity.ipynb) △

windowing / lookup が必要な場合だけ次へ進みます。

- [Unary Iteration](notebooks/04_bloqs_library/01_concepts/02_unary_iteration.ipynb) △
- [QROM](notebooks/04_bloqs_library/07_data_loading/01_qrom.ipynb) △
- [SelectSwapQROM](notebooks/04_bloqs_library/07_data_loading/02_select_swap_qrom.ipynb) △
- [QROAMClean](notebooks/04_bloqs_library/07_data_loading/03_qroam_clean.ipynb) △

基本ゲートは必要時に [Basic Gates](notebooks/04_bloqs_library/08_basic_gates/) を参照します。

### 6. Physical resource estimation

論理リソース推定の完成後に [Quantum Computer Architectures](notebooks/02_architectures/) へ進みます。

1. [Physical Cost Model](notebooks/02_architectures/01_physical_cost_model.ipynb) ◎
2. [Beverland et al. Model](notebooks/02_architectures/02_beverland_model.ipynb) ◎
3. [Microsoft Resource Estimator](notebooks/02_architectures/04_msft_resource_estimator.ipynb) △

THC FeMoco は今回の学習対象外です。

### 7. 最終検証・論文用

- [Drawing Call Graphs](notebooks/03_advanced/09_drawing_call_graphs.ipynb) ○
- [Cross-checking Classical Simulation](notebooks/03_advanced/11_cross_checking_classical_simulation.ipynb) ○
- [Qualtran + QREF & Bartiq](notebooks/03_advanced/04_qref_bartiq.ipynb) △
- [Microsoft Resource Estimator](notebooks/02_architectures/04_msft_resource_estimator.ipynb) △

## 検証

追加した notebook は、英語タイトル、対応する公式ドキュメントへのリンク、実装用の英語小節見出しだけを置いた skeleton です。

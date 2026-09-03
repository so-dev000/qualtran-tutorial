# Qualtran Tutorial: GF(p^r) DLP Learning Roadmap

Qualtran で GF(p^r) 上の Shor 型 DLP 回路を構築し、論理・物理リソースを見積もるための notebook 集です。

優先度は `◎◎ / ◎ / ○ / △ / ×` の順です。`×` は今回読まない項目です。

## Setup

```bash
uv sync
uv run jupyter lab
```

[Setup and Sanity Check](notebooks/00_setup.ipynb)

## I. Fundamentals

最初にすべて完了します。

1. ◎ [Bloqs Tutorial](notebooks/01_fundamentals/01_bloqs_tutorial.ipynb)
2. ◎ [Data Types](notebooks/01_fundamentals/02_data_types.ipynb)
3. ○ [Protocols](notebooks/01_fundamentals/03_protocols.ipynb)
4. ◎ [Classical Simulation](notebooks/01_fundamentals/04_classical_simulation.ipynb)
5. × [Tensor Simulation](notebooks/01_fundamentals/05_tensor_simulation.ipynb)
6. ◎ [The Call Graph Protocol](notebooks/01_fundamentals/06_call_graph.ipynb)
7. ◎ [Qubit Counts](notebooks/01_fundamentals/07_qubit_counts.ipynb)
8. ○ [Adjoint](notebooks/01_fundamentals/08_adjoint.ipynb)
9. ◎ [Controlled](notebooks/01_fundamentals/09_controlled.ipynb)

## II. Shor / DLP Structure in Qualtran

10. ◎ Concepts
    - [Factoring and Shor's Algorithm](notebooks/02_shor_dlp_structure/10_concepts/01_factoring_and_shor.ipynb)
11. ◎ Root Bloqs
    - [Elliptic Curve Cryptography](notebooks/02_shor_dlp_structure/11_root_bloqs/01_elliptic_curve_cryptography.ipynb)
12. ○ Rotations
    - [Textbook QFT](notebooks/02_shor_dlp_structure/12_rotations/01_textbook_qft.ipynb)
    - [Textbook Quantum Phase Estimation](notebooks/02_shor_dlp_structure/12_rotations/02_textbook_qpe.ipynb)

ECC notebook は楕円曲線算術そのものではなく、`FindECCPrivateKey → ECPhaseEstimateR → ECAddR` という DLP の上位構造を読むために使います。

## III. F_p Arithmetic

GF(p^r) 実装の係数体となる F_p 算術を学びます。

13. ◎ Arithmetic
    - ◎ [Addition](notebooks/03_fp_arithmetic/13_arithmetic/01_addition.ipynb)
    - ◎ [Controlled Addition](notebooks/03_fp_arithmetic/13_arithmetic/02_controlled_addition.ipynb)
    - ○ [Negation](notebooks/03_fp_arithmetic/13_arithmetic/03_negation.ipynb)
    - ◎ [Subtraction](notebooks/03_fp_arithmetic/13_arithmetic/04_subtraction.ipynb)
    - ○ [Controlled Add-or-Subtract](notebooks/03_fp_arithmetic/13_arithmetic/05_controlled_add_or_subtract.ipynb)
    - ○ [Multiplication](notebooks/03_fp_arithmetic/13_arithmetic/06_multiplication.ipynb)
    - ○ [Comparison](notebooks/03_fp_arithmetic/13_arithmetic/07_comparison.ipynb)
14. ◎◎ Modular Arithmetic
    - ◎ [Modular Addition](notebooks/03_fp_arithmetic/14_modular_arithmetic/01_modular_addition.ipynb)
    - ◎ [Modular Subtraction](notebooks/03_fp_arithmetic/14_modular_arithmetic/02_modular_subtraction.ipynb)
    - ◎ [Modular Multiplication](notebooks/03_fp_arithmetic/14_modular_arithmetic/03_modular_multiplication.ipynb)
    - × [Modular Division](notebooks/03_fp_arithmetic/14_modular_arithmetic/04_modular_division.ipynb)
    - ○ [Factoring RSA](notebooks/03_fp_arithmetic/14_modular_arithmetic/05_factoring_rsa.ipynb)

## IV. GF(p^r) Representation

15. ◎ Polynomials over Galois Fields
    - [Polynomials over GF(p^m) - Split and Join](notebooks/04_gf_pr_representation/15_gf_polynomials/01_gf_poly_split_join.ipynb)
16. ○ GF Arithmetic
    - ◎ [GF(2^m) Multiplication](notebooks/04_gf_pr_representation/16_gf_arithmetic/01_gf2_multiplication.ipynb)
    - ○ [GF(2^m) Addition](notebooks/04_gf_pr_representation/16_gf_arithmetic/02_gf2_addition.ipynb)
    - 参照 [GF(2^m) Add Constant](notebooks/04_gf_pr_representation/16_gf_arithmetic/03_gf2_add_constant.ipynb)
    - × [GF(2^m) Square](notebooks/04_gf_pr_representation/16_gf_arithmetic/04_gf2_square.ipynb)
    - × [GF(2^m) Inverse](notebooks/04_gf_pr_representation/16_gf_arithmetic/05_gf2_inverse.ipynb)

GF(2^m) の notebook は直接流用するためではなく、GF(p^r) Bloq の実装例として読みます。

## V. Implement the Baseline

ここでドキュメントを読むのを一度止め、[GF(p^r) Shor-DLP Implementation](notebooks/05_dlp_implementation/01_shor_dlp_implementation.ipynb) に baseline を実装します。

## VI. Advanced Topics

Baseline 完成後に進みます。

17. ◎ [Composite Bloq Manipulation](notebooks/06_advanced_topics/17_composite_bloq_manipulation.ipynb)
18. ◎ [Bloqs with Specialized Controlled Implementations](notebooks/06_advanced_topics/18_specialized_controlled_implementations.ipynb)
19. ○ [Propagating the Adjoint](notebooks/06_advanced_topics/19_propagating_the_adjoint.ipynb)
20. △ [T Complexity](notebooks/06_advanced_topics/20_t_complexity.ipynb)
21. △ [Drawing Call Graphs](notebooks/06_advanced_topics/21_drawing_call_graphs.ipynb)
22. △ [Cross-checking Classical Simulation](notebooks/06_advanced_topics/22_cross_checking_classical_simulation.ipynb)

今回読まないページ: [Cirq Interoperability](notebooks/06_advanced_topics/cirq_interoperability.ipynb)、[Gate with Registers](notebooks/06_advanced_topics/gate_with_registers.ipynb)、[Musical Score](notebooks/06_advanced_topics/musical_score.ipynb)、[Documenting Bloqs](notebooks/06_advanced_topics/documenting_bloqs.ipynb)

## VII. Advanced Arithmetic Optimization

必要になった場合だけ進みます。

23. △ Concepts
    - [Unary Iteration](notebooks/07_arithmetic_optimization/23_concepts/01_unary_iteration.ipynb)
    - [T Complexity Of Comparison Gates](notebooks/07_arithmetic_optimization/23_concepts/02_t_complexity_of_comparison_gates.ipynb)
24. △ Other
    - [QROM](notebooks/07_arithmetic_optimization/24_other/01_qrom.ipynb)
    - [SelectSwapQROM](notebooks/07_arithmetic_optimization/24_other/02_select_swap_qrom.ipynb)
    - [Advanced QROM / QROAM](notebooks/07_arithmetic_optimization/24_other/03_qroam_clean.ipynb)

## VIII. Quantum Computer Architectures

論理リソース推定の完成後に進みます。

25. ◎◎ [Architecture-dependent physical costs](notebooks/08_architectures/25_physical_cost_model.ipynb)
26. ◎ [Beverland et al. Model](notebooks/08_architectures/26_beverland_model.ipynb)
- △ [Interop with Microsoft Resource Estimator](notebooks/08_architectures/msft_resource_estimator.ipynb)
- × [THC FeMoco Compilation](notebooks/08_architectures/thc_femoco.ipynb)

## IX. Out of Scope

Chemistry、Block Encoding、Qubitization、Hamiltonian Simulation、Trotter、Quantum Walk PE、state preparation、Kikuchi、および chemistry resource estimation は今回の notebook 集には含めません。

## Notebook Format

Skeleton notebook は、英語タイトル、対応する Qualtran 公式ドキュメントへのリンク、ロードマップ直下の英語小節見出しだけで構成しています。既に学習内容が記入されている Fundamentals notebook のコードセルと実行結果は保持しています。

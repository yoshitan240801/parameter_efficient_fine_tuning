---
marp: true
theme: default
paginate: true
---

# MNISTデータセットを用いたニューラルネットワークとLoRAの実装

---

# 基本的なニューラルネットワークの構築と学習

- **ネットワーク構造**
  ```
  Input(784) → Linear(1000) → ReLU → Linear(2000) → ReLU → Linear(10)
  ```

- **学習設定**
  - Optimizer: Adam (lr=0.001)
  - Loss: CrossEntropyLoss
  - Batch size: 100

---

# LoRAの実装と適用

- **LoRAの構造**
  - 各Linear層に対してLoRAを適用
  - rank=1, alpha=1で設定
  - A∈R^(rank×post_dim), B∈R^(pre_dim×rank)

- **LoRAの更新方法**
  1. 元のモデルパラメータを固定
  2. LoRAパラメータのみを更新対象に
  3. 誤認識の多い数字のデータのみで再学習

---

# 処理の流れ

1. 基本モデルの学習と評価
2. 誤認識の多い数字の特定
3. LoRAの適用と再学習
   - 全データ
   - データの一部(1/8)
4. 性能評価と比較

- 各段階で推論を実行し、正解率と誤認識パターンを確認
- LoRAパラメータの初期化による元モデルへの復帰も確認
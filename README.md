# WIP

眼球運動に関する6つの視覚タスクを解く単一の計算モデルを作成します。特に並列性・積分・異なる時間スケール・記憶等に着目して開発を行います。

Susumu OTA



# 視覚タスク

https://github.com/wbap/oculoenv/blob/master/README.md#tasks より引用。

### Point to taget

![point to target task](https://github.com/wbap/oculoenv/raw/master/docs/images/point_to_target_task.png)

> The agent is required to move the gaze point to the target (small or large E) with avoinding the lure object (small or large rotated E).

単純なA2C+CNNで学習させると大きいE(報酬1)をポイントするように収束してしまう(計算時間は2時間程度)。小さいE(報酬2)をポイントしたときの記憶を持つ必要がある。外部記憶モデルが参考になるかもしれない。

### Change detection

![change detection task](https://github.com/wbap/oculoenv/raw/master/docs/images/change_detection_task.png)

> The agent is required to detect whether the combination of objects are changed after the blank period. If objects are changed agent should choose left black target and otherwise should choose right.

記憶モデルが必要。

### Visual search

![visual search task](https://github.com/wbap/oculoenv/raw/master/docs/images/visual_search_task.png)

> The agent is required to detect whether there is magenta T shape on the screen or not.
If there is, the agent should choose right bottom black target and otherwise left bottom one.

### Odd one out

![odd one out task](https://github.com/wbap/oculoenv/raw/master/docs/images/odd_one_out_task.png)

> The agent is required to move the gaze point to the target which has different property from others (color, shape or movement).

色や形の変わったターゲットについては、おそらく従来のCNNでもある程度検出可能。運動するターゲットについては時間軸に関するモデルが必要。サリエンシーマップで対応可能か？

単純なA2C+CNNで学習させると8時間学習させても収束せず(精度はランダムの2倍程度)。


### Multiple object tracking

![multiple object traking task](https://github.com/wbap/oculoenv/raw/master/docs/images/multiple_object_tracking_task.png)

> The agent should answer whether the last blue dot has started as green or not.
If yes, the agent should choose right bottom black target and otherwise left bottom one.

難易度高そう。記憶モデルが必要。

### Random dot motion discrimination

![random dot motion discrimination task](https://github.com/wbap/oculoenv/raw/master/docs/images/random_dot_task.png)

> The agent is required to detect the direction of the moving dots while some portion of the dots has non-coherent random movement. The agent should answer the direction by moving the gaze point to the arrow objects.

サリエンシーマップでどこまで動きの特徴をとれるのか？


# 参考

## 視覚タスク

- oculoenv
https://github.com/wbap/oculoenv

- Psychlab
https://arxiv.org/abs/1801.08116

## サリエンシーマップ

- サリエンシー・マップの視覚探索解析への応用
https://www.jstage.jst.go.jp/article/jnns/21/1/21_3/_pdf/-char/ja

- How is visual salience computed in the brain? Insights from behaviour,neurobiology and modelling
http://rstb.royalsocietypublishing.org/content/royptb/372/1714/20160113.full.pdf

## 外部記憶

- NTM (2014)
Neural Turing Machines
http://arxiv.org/abs/1410.5401

- DNC (2016)
Differentiable Neural Computer
https://www.nature.com/articles/nature20101
https://github.com/deepmind/dnc

- MERLIN (2018)
Memory, RL, and Inference Network
https://arxiv.org/abs/1803.10760

## 並列化

- GORILA
General Reinforcement Learning Architecture

- A3C
Asynchronous Advantage Actor-Critic

## 補助タスク

- UNREAL (2016)
Reinforcement Learning with Unsupervised Auxiliary Tasks
https://arxiv.org/abs/1611.05397

## 方策関数更新のクリッピング

- PPO
Proximal Policy Optimization Algorithms
https://arxiv.org/abs/1707.06347


## 再利用・標準化

- OpenAI Gym
https://github.com/openai/gym

- OpenAI Baselines
https://github.com/openai/baselines

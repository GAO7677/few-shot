# FLUX.2 LoRA 生成示例

使用仓库中的 [8 张 RarePlanes 示例图片](../../asset/my_data) 训练：rank=4、400 steps。以下两批共用这次训练的同一份 LoRA，区别在于推理时如何指定 prompt。

| 批次 | Prompt 设置 | 10张图的分配 |
|---|---|---|
| `20261012_062704_582709/lora` | 省略 `--prompt`，按训练图片顺序循环使用对应 caption | 6张使用中型民用飞机描述，4张使用小型民用飞机描述 |
| `20261012_063050_103424/lora` | 通过 `--prompt` 手动指定中型民用飞机描述 | 10张均使用中型民用飞机描述 |

第二批用于验证已有权重下的手动 prompt 生成流程。两批的 seed 均为 `0–9`，分辨率均为 `512×512`，采样均为 `50 steps`、`guidance_scale=4.0`。每张图都有同名 JSON，记录实际使用的 prompt、seed 和生成参数。

**路径约定：** JSON 中的文件路径均相对于该 JSON 所在目录；`image` 指向同目录图片。`base_model` 预留到仓库根目录的 `models/FLUX.2-klein-base-4B/`，`adapter_path` 预留到本目录的 `adapter/`，两处权重均未上传。

图片保持原始字节。逐图 JSON 仅保留12项必要信息：图片名、prompt、seed、模型、底座路径、LoRA路径、训练步数、宽高、采样步数、guidance scale 和 scheduler。

## 20261012_062704_582709

Seed `0–3、8–9` 使用 P1，seed `4–7` 使用 P2。这里按8张训练图片的 caption 顺序循环，因此两种描述的图数为6张和4张。

P1：`an overhead satellite RGB image of a medium civil transport aircraft at an airport`

P2：`an overhead satellite RGB image of small civil aircraft at an airport`

| 生成图 | Seed | Prompt | 元数据 |
|---|---:|---|---|
| <img src="generations/20261012_062704_582709/lora/000000.png" width="192" alt="seed 0"> | 0 | P1 | [JSON](generations/20261012_062704_582709/lora/000000.json) |
| <img src="generations/20261012_062704_582709/lora/000001.png" width="192" alt="seed 1"> | 1 | P1 | [JSON](generations/20261012_062704_582709/lora/000001.json) |
| <img src="generations/20261012_062704_582709/lora/000002.png" width="192" alt="seed 2"> | 2 | P1 | [JSON](generations/20261012_062704_582709/lora/000002.json) |
| <img src="generations/20261012_062704_582709/lora/000003.png" width="192" alt="seed 3"> | 3 | P1 | [JSON](generations/20261012_062704_582709/lora/000003.json) |
| <img src="generations/20261012_062704_582709/lora/000004.png" width="192" alt="seed 4"> | 4 | P2 | [JSON](generations/20261012_062704_582709/lora/000004.json) |
| <img src="generations/20261012_062704_582709/lora/000005.png" width="192" alt="seed 5"> | 5 | P2 | [JSON](generations/20261012_062704_582709/lora/000005.json) |
| <img src="generations/20261012_062704_582709/lora/000006.png" width="192" alt="seed 6"> | 6 | P2 | [JSON](generations/20261012_062704_582709/lora/000006.json) |
| <img src="generations/20261012_062704_582709/lora/000007.png" width="192" alt="seed 7"> | 7 | P2 | [JSON](generations/20261012_062704_582709/lora/000007.json) |
| <img src="generations/20261012_062704_582709/lora/000008.png" width="192" alt="seed 8"> | 8 | P1 | [JSON](generations/20261012_062704_582709/lora/000008.json) |
| <img src="generations/20261012_062704_582709/lora/000009.png" width="192" alt="seed 9"> | 9 | P1 | [JSON](generations/20261012_062704_582709/lora/000009.json) |

## 20261012_063050_103424

Seed `0–9` 全部使用 P1。

P1：`an overhead satellite RGB image of a medium civil transport aircraft at an airport`

| 生成图 | Seed | Prompt | 元数据 |
|---|---:|---|---|
| <img src="generations/20261012_063050_103424/lora/000000.png" width="192" alt="seed 0"> | 0 | P1 | [JSON](generations/20261012_063050_103424/lora/000000.json) |
| <img src="generations/20261012_063050_103424/lora/000001.png" width="192" alt="seed 1"> | 1 | P1 | [JSON](generations/20261012_063050_103424/lora/000001.json) |
| <img src="generations/20261012_063050_103424/lora/000002.png" width="192" alt="seed 2"> | 2 | P1 | [JSON](generations/20261012_063050_103424/lora/000002.json) |
| <img src="generations/20261012_063050_103424/lora/000003.png" width="192" alt="seed 3"> | 3 | P1 | [JSON](generations/20261012_063050_103424/lora/000003.json) |
| <img src="generations/20261012_063050_103424/lora/000004.png" width="192" alt="seed 4"> | 4 | P1 | [JSON](generations/20261012_063050_103424/lora/000004.json) |
| <img src="generations/20261012_063050_103424/lora/000005.png" width="192" alt="seed 5"> | 5 | P1 | [JSON](generations/20261012_063050_103424/lora/000005.json) |
| <img src="generations/20261012_063050_103424/lora/000006.png" width="192" alt="seed 6"> | 6 | P1 | [JSON](generations/20261012_063050_103424/lora/000006.json) |
| <img src="generations/20261012_063050_103424/lora/000007.png" width="192" alt="seed 7"> | 7 | P1 | [JSON](generations/20261012_063050_103424/lora/000007.json) |
| <img src="generations/20261012_063050_103424/lora/000008.png" width="192" alt="seed 8"> | 8 | P1 | [JSON](generations/20261012_063050_103424/lora/000008.json) |
| <img src="generations/20261012_063050_103424/lora/000009.png" width="192" alt="seed 9"> | 9 | P1 | [JSON](generations/20261012_063050_103424/lora/000009.json) |

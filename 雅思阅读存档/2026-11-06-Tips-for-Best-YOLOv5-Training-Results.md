# Tips for Best YOLOv5 Training Results

- 导入日期：2026-11-06
- 类型：粘贴 / 原文

## 原文 / 译文

# Tips for Best YOLOv5 Training Results

> 获得最佳 YOLOv5 训练效果的技巧

This guide explains how to produce the best mAP and training results with YOLOv5.

> 本指南介绍如何使用 YOLOv5 获得最佳的 mAP 和训练结果。

Most of the time, good results can be obtained with no changes to the models or training settings, **provided your dataset is sufficiently large and well labeled**. If at first you don't get good results, there are steps you might be able to take to improve, but we always recommend users **first train with all default settings** before considering any changes. This helps establish a performance baseline and spot areas for improvement.

> 在大多数情况下，只要数据集足够大且标注良好，无需改动模型或训练设置就能获得不错的结果。如果一开始效果不理想，你可以采取一些步骤来改进，但我们始终建议用户在考虑任何改动之前，先使用全部默认设置进行训练。这有助于建立性能基线，并发现可以改进的地方。

If you have questions about your training results, **provide as much information as possible** to get a helpful response, including results plots (train losses, val losses, P, R, mAP), PR curve, confusion matrix, training mosaics, test results and dataset statistics images such as labels.png. All of these are located in your `project/name` directory, typically `yolov5/runs/train/exp`.

> 如果你对训练结果有疑问，请尽可能提供更多信息以获得有用的回复，包括结果图（训练损失、验证损失、P、R、mAP）、PR 曲线、混淆矩阵、训练马赛克图、测试结果以及数据集统计图像（如 labels.png）。所有这些文件都位于你的 project/name 目录中，通常是 yolov5/runs/train/exp。

The sections below cover the main factors that affect YOLOv5 training results.

> 下面的各部分涵盖了影响 YOLOv5 训练结果的主要因素。

## Dataset

> 数据集

- **Images per class.** ≥ 1500 images per class recommended
- **Instances per class.** ≥ 10000 instances (labeled objects) per class recommended
- **Image variety.** Must be representative of deployed environment. For real-world use cases we recommend images from different times of day, different seasons, different weather, different lighting, different angles, different sources (scraped online, collected locally, different cameras) etc.
- **Label consistency.** All instances of all classes in all images must be labeled. Partial labeling will not work.
- **Label accuracy.** Labels must closely enclose each object. No space should exist between an object and its bounding box. No objects should be missing a label.
- **Train/val split discipline.** Ensure that validation and test images never appear in the training set to avoid overly optimistic metrics. Keep class distributions similar between the splits.
- **Label verification.** View the `train_batch*.jpg` mosaics on train start to verify your labels appear correct.
- **Background images.** Background images are images with no objects that are added to a dataset to reduce False Positives (FP). We recommend about 0-10% background images to help reduce FPs (COCO has 1000 background images for reference, 1% of the total). No labels are required for background images.

> - 每类图像数量：建议每类不少于 1500 张图像。
> - 每类实例数量：建议每类不少于 10000 个实例（已标注的目标）。
> - 图像多样性：必须能代表实际部署环境。对于真实应用场景，我们建议使用来自不同时间段、不同季节、不同天气、不同光照、不同角度、不同来源（网络抓取、本地采集、不同相机）等的图像。
> - 标签一致性：所有图像中所有类别的所有实例都必须被标注。部分标注是行不通的。
> - 标签准确性：标签必须紧密包围每个目标。目标与其边界框之间不应有空隙。不应有任何目标缺少标签。
> - 训练/验证划分的严格性：确保验证和测试图像绝不出现在训练集中，以避免指标过于乐观。保持各划分之间的类别分布相近。
> - 标签验证：在训练开始时查看 train_batch*.jpg 马赛克图，以确认标签显示正确。
> - 背景图像：背景图像是不含任何目标、被加入数据集以减少误检（FP）的图像。我们建议使用约 0-10% 的背景图像来帮助减少误检（作为参考，COCO 有 1000 张背景图像，占总数的 1%）。背景图像不需要标签。

## Model Selection

> 模型选择

Larger models like YOLOv5x and YOLOv5x6 will produce better results in nearly all cases, but have more parameters, require more CUDA memory to train, and are slower to run. For **mobile** deployments we recommend YOLOv5s/m, for **cloud** deployments we recommend YOLOv5l/x.

> 在几乎所有情况下，YOLOv5x 和 YOLOv5x6 等较大的模型会产生更好的结果，但它们参数更多，训练时需要更多 CUDA 内存，运行速度也更慢。对于移动端部署，我们推荐 YOLOv5s/m；对于云端部署，我们推荐 YOLOv5l/x。

- **Start from Pretrained weights.** Recommended for small to medium-sized datasets (e.g. VOC, VisDrone, GlobalWheat). Pass the name of the model to the `--weights` argument. Models download automatically from the latest YOLOv5 release.

> - 从预训练权重开始：推荐用于小型到中型数据集（如 VOC、VisDrone、GlobalWheat）。将模型名称传给 --weights 参数。模型会自动从最新的 YOLOv5 版本下载。

    ```bash
    python train.py --data custom.yaml --weights yolov5s.pt
    python train.py --data custom.yaml --weights yolov5m.pt
    python train.py --data custom.yaml --weights yolov5l.pt
    python train.py --data custom.yaml --weights yolov5x.pt
    python train.py --data custom.yaml --weights custom_pretrained.pt
    ```

>     （代码示例）

- **Start from Scratch.** Recommended for large datasets (e.g. COCO, Objects365, OIv6). Pass the model architecture YAML you are interested in, along with an empty `--weights ''` argument:

> - 从零开始训练：推荐用于大型数据集（如 COCO、Objects365、OIv6）。传入你感兴趣的模型架构 YAML，并搭配一个空的 --weights '' 参数：

    ```bash
    python train.py --data custom.yaml --weights '' --cfg yolov5s.yaml
    python train.py --data custom.yaml --weights '' --cfg yolov5m.yaml
    python train.py --data custom.yaml --weights '' --cfg yolov5l.yaml
    python train.py --data custom.yaml --weights '' --cfg yolov5x.yaml
    ```

>     （代码示例）

## Training Settings

> 训练设置

Before modifying anything, **first train with default settings to establish a performance baseline**. A full list of train.py settings can be found in the train.py argparser.

> 在修改任何内容之前，请先使用默认设置训练以建立性能基线。train.py 的完整设置列表可以在 train.py 的参数解析器中找到。

- **Epochs.** Start with 300 epochs. If this overfits early then you can reduce epochs. If overfitting does not occur after 300 epochs, train longer, e.g. 600 or 1200 epochs.
- **Image size.** COCO trains at native resolution of `--img 640`, though due to the large number of small objects in the dataset it can benefit from training at higher resolutions such as `--img 1280`. If there are many small objects then custom datasets will benefit from training at native or higher resolution. Best inference results are obtained at the same `--img` as the training was run at, e.g. if you train at `--img 1280` you should also test and detect at `--img 1280`.
- **Batch size.** Use the largest `--batch-size` that your hardware allows for. Small batch sizes produce poor batch normalization statistics and should be avoided. You can use `--batch-size -1` to automatically select the optimal batch size for your GPU.
- **Learning rate.** The default learning rate schedule works well in most cases. For faster convergence, you can try using the `--cos-lr` flag to enable cosine learning rate scheduling, which gradually reduces the learning rate following a cosine curve over epochs.
- **Data augmentation.** YOLOv5 includes various augmentation techniques like mosaic, which combines multiple training images. Adjust augmentation strength via the `mosaic` hyperparameter in your `--hyp` file to help stabilize training.
- **Hyperparameters.** Default hyperparameters are in hyp.scratch-low.yaml. We recommend you train with default hyperparameters first before thinking of modifying any. In general, increasing augmentation hyperparameters will reduce and delay overfitting, allowing for longer trainings and higher final mAP. Reduction in loss component gain hyperparameters like `hyp['obj']` will help reduce overfitting in those specific loss components. For an automated method of optimizing these hyperparameters, see our Hyperparameter Evolution Tutorial.
- **Mixed precision training.** YOLOv5 enables Automatic Mixed Precision (AMP) automatically when a supported GPU is detected, speeding up training and reducing memory usage without sacrificing model accuracy.
- **Multi-GPU training.** If you have multiple GPUs, launch DistributedDataParallel training with `python -m torch.distributed.run --nproc_per_node 4 train.py ... --device 0,1,2,3`, which can significantly reduce training time.
- **Early stopping.** Use `--patience 50` to stop training if validation metrics don't improve for 50 epochs, saving time and preventing overfitting.

> - 训练轮数：从 300 轮开始。如果过早出现过拟合，可以减少轮数。如果 300 轮后没有出现过拟合，则训练更久，例如 600 或 1200 轮。
> - 图像尺寸：COCO 以 --img 640 的原生分辨率训练，不过由于该数据集中小目标很多，用 --img 1280 等更高分辨率训练可能会受益。如果小目标很多，自定义数据集也会从原生或更高分辨率训练中受益。最佳推理结果是在与训练相同的 --img 下获得的，例如如果你以 --img 1280 训练，也应以 --img 1280 进行测试和检测。
> - 批量大小：使用硬件允许的最大 --batch-size。小批量会产生较差的批归一化统计量，应当避免。你可以使用 --batch-size -1 为你的 GPU 自动选择最优批量大小。
> - 学习率：默认的学习率调度在大多数情况下效果良好。为了更快收敛，你可以尝试使用 --cos-lr 标志来启用余弦学习率调度，它会按照余弦曲线在各轮次中逐步降低学习率。
> - 数据增强：YOLOv5 包含多种增强技术，如马赛克增强（将多张训练图像组合在一起）。通过 --hyp 文件中的 mosaic 超参数调整增强强度，有助于稳定训练。
> - 超参数：默认超参数位于 hyp.scratch-low.yaml 中。我们建议你先使用默认超参数训练，再考虑修改。总体而言，增加数据增强超参数会减少并推迟过拟合，从而允许更长时间的训练和更高的最终 mAP。降低 hyp['obj'] 等损失分量增益超参数，有助于减少这些特定损失分量的过拟合。如需自动优化这些超参数的方法，请参阅我们的超参数进化教程。
> - 混合精度训练：当检测到受支持的 GPU 时，YOLOv5 会自动启用自动混合精度（AMP），在不牺牲模型精度的情况下加快训练速度并减少内存占用。
> - 多 GPU 训练：如果你有多块 GPU，可以使用 python -m torch.distributed.run --nproc_per_node 4 train.py ... --device 0,1,2,3 启动分布式数据并行训练，这可以显著缩短训练时间。
> - 提前停止：使用 --patience 50，如果验证指标在 50 轮内没有改善就停止训练，既节省时间又防止过拟合。

## Advanced Optimization Techniques

> 高级优化技术

- **Transfer learning.** For specialized datasets, start with pretrained weights and optionally freeze layers with `--freeze` to adapt the model to your specific task.
- **Model pruning.** After training, consider pruning your model to zero out redundant weights with little loss in accuracy, then deploy it with a sparsity-aware runtime to realize speedups.
- **Model ensemble.** For critical applications, train multiple models with different configurations and ensemble their predictions for improved accuracy.
- **Test-time augmentation.** Enable TTA during inference with `--augment` to improve prediction accuracy by merging predictions from flipped and rescaled versions of the input image.

> - 迁移学习：对于专门的数据集，从预训练权重开始，并可选择使用 --freeze 冻结部分层，以使模型适应你的特定任务。
> - 模型剪枝：训练之后，可以考虑对模型进行剪枝，将冗余权重置零而几乎不损失精度，然后用支持稀疏性的运行时部署，以实现加速。
> - 模型集成：对于关键应用，使用不同配置训练多个模型，并集成它们的预测结果以提高精度。
> - 测试时增强：在推理时使用 --augment 启用 TTA，通过合并翻转和缩放后的输入图像的预测结果来提高预测精度。

## Further Reading

> 延伸阅读

If you'd like to know more, a good place to start is Karpathy's A Recipe for Training Neural Networks, which has ideas for training that apply broadly across all ML domains.

> 如果你想了解更多，一个很好的起点是 Karpathy 的《训练神经网络的秘诀》，其中的训练思路广泛适用于所有机器学习领域。

Good luck, and let us know if you have any other questions.

> 祝你好运，如果还有其他问题，请告诉我们。

## FAQ

> 常见问题

### How do I know if my model is overfitting?

> 我如何知道我的模型是否过拟合？

Your model may be overfitting if the training loss continues to decrease while validation loss starts to increase. Monitor the validation mAP - if it plateaus or decreases while training loss keeps improving, that's a sign of overfitting. Solutions include adding more training data, increasing data augmentation, or applying regularization techniques.

> 如果训练损失持续下降而验证损失开始上升，你的模型可能出现了过拟合。监测验证 mAP——如果它在训练损失持续改善的同时趋于平稳或下降，就是过拟合的迹象。解决办法包括增加更多训练数据、加强数据增强或应用正则化技术。

### What's the optimal batch size for training YOLOv5?

> 训练 YOLOv5 的最优批量大小是多少？

The optimal batch size depends on your GPU memory. Larger batch sizes generally provide better batch normalization statistics and training stability. Use the largest batch size your hardware can handle without running out of memory. You can use `--batch-size -1` to automatically determine the optimal batch size for your setup.

> 最优批量大小取决于你的 GPU 内存。较大的批量通常能提供更好的批归一化统计量和训练稳定性。使用你的硬件在不耗尽内存的前提下能处理的最大批量。你可以使用 --batch-size -1 为你的配置自动确定最优批量大小。

### How can I speed up YOLOv5 training?

> 如何加快 YOLOv5 的训练速度？

To speed up training, try: using multiple GPUs with DDP, caching your dataset with `--cache`, and optimizing your batch size (mixed precision is enabled automatically on supported GPUs). Also consider using a smaller model variant like YOLOv5s if absolute accuracy isn't critical.

> 要加快训练，可以尝试：使用 DDP 进行多 GPU 训练、用 --cache 缓存数据集，以及优化批量大小（在受支持的 GPU 上会自动启用混合精度）。如果绝对精度不是关键，也可以考虑使用更小的模型变体，如 YOLOv5s。

## 生词

| 单词 | 音标 | 词性 | 释义 | 例句 |
|---|---|---|---|---|
| baseline | /ˈbeɪslaɪn/ | n. | 基线，基准 | We need a baseline to compare the results. |
| representative | /ˌrepriˈzentətɪv/ | adj. | 有代表性的 | The sample must be representative of the whole population. |
| consistency | /kənˈsɪstənsi/ | n. | 一致性 | Consistency is important in scientific experiments. |
| discipline | /ˈdɪsəplɪn/ | n. | 严格的规范；纪律 | Good data discipline prevents errors. |
| optimistic | /ˌɑːptɪˈmɪstɪk/ | adj. | 乐观的 | The forecast was overly optimistic. |
| deploy | /dɪˈplɔɪ/ | v. | 部署，投入使用 | The company will deploy the new system next year. |
| enclose | /ɪnˈkloʊz/ | v. | 围住，包围 | A fence encloses the garden. |
| redundant | /rɪˈdʌndənt/ | adj. | 多余的，冗余的 | Remove redundant information from the report. |
| stabilize | /ˈsteɪbəlaɪz/ | v. | 使稳定 | Measures were taken to stabilize the economy. |
| plateau | /plæˈtoʊ/ | v. | 进入平稳期，停止增长 | Sales plateaued after two years of growth. |
| convergence | /kənˈvɜːrdʒəns/ | n. | 收敛，趋同 | The convergence of technologies changed the industry. |
| significantly | /sɪɡˈnɪfɪkəntli/ | adv. | 显著地 | Prices have risen significantly this year. |
| optimal | /ˈɑːptɪməl/ | adj. | 最优的 | This is the optimal solution to the problem. |
| specialized | /ˈspeʃəlaɪzd/ | adj. | 专门的，专业化的 | The job requires specialized knowledge. |
| gradually | /ˈɡrædʒuəli/ | adv. | 逐渐地 | The temperature gradually dropped overnight. |
| spot areas | /spɑt ˈɛriəz/ | phrase | 发现(需要改进的)方面;找出领域 | This helps establish a performance baseline and spot areas for improvement. |
| scrape | /skreɪp/ | v. | (用程序)抓取、爬取(网络数据) | For real-world use cases we recommend images from different times of day, different seasons, different weather, different lighting, different angles, different sources (scraped online, collected locally, different cameras) etc. |
| prune | /pruːn/ | v. | 剪枝(移除神经网络中冗余的权重或连接以压缩模型) | - **Model pruning.** After training, consider pruning your model to zero out redundant weights with little loss in accuracy, then deploy it with a sparsity-aware runtime to realize speedups. |
| speedup | /ˈspiːdˌʌp/ | n. | 加速;速度提升(指运行速度的提高) | - **Model pruning.** After training, consider pruning your model to zero out redundant weights with little loss in accuracy, then deploy it with a sparsity-aware runtime to realize speedups. |

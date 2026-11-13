# Key Steps in a Computer Vision Project

- 导入日期：2026-11-05
- 类型：粘贴 / 原文

## 原文 / 译文

Building a computer vision project means moving through a clear sequence of stages: defining your goals, collecting and annotating data, training and evaluating a model, and deploying and maintaining it in production. This guide walks through each step in order and explains why it matters, so you can plan and run your own project with confidence.

> 计算机视觉项目的建设意味着要经历一系列清晰的阶段:确定目标、收集并标注数据、训练并评估模型,以及在生产环境中部署并维护模型。本指南按顺序讲解每一步,并解释其重要性,让你能够有信心地规划和运行自己的项目。

Computer vision is a subfield of artificial intelligence (AI) that helps computers see and understand the world like humans do. It processes and analyzes images or videos to extract information, recognize patterns, and make decisions based on that data.

> 计算机视觉是人工智能(AI)的一个子领域,帮助计算机像人类一样看见并理解世界。它处理和分析图像或视频,以提取信息、识别模式,并基于这些数据做出决策。

Computer vision techniques like object detection, image classification, and instance segmentation can be applied across various industries, from autonomous driving to medical imaging to gain valuable insights.

> 目标检测、图像分类和实例分割等计算机视觉技术可应用于从自动驾驶到医学影像的各个行业,从而获得有价值的洞见。

An Overview of a Computer Vision Project

> 计算机视觉项目概览

Before discussing the details of each step involved in a computer vision project, let's look at the overall process. If you started a computer vision project today, you'd take the following steps:

> 在讨论计算机视觉项目每个步骤的细节之前,先来看看整体流程。如果你今天开始一个计算机视觉项目,你会采取以下步骤:

Your first priority is to understand your project's requirements.

> 你的首要任务是了解项目的需求。

Then, you collect and accurately label the images that will help train your model.

> 然后,收集并准确标注有助于训练模型的图像。

Next, you clean and augment your data to prepare it for model training.

> 接着,清洗并扩充数据,为模型训练做好准备。

After training, you thoroughly evaluate and test your model to make sure it performs consistently under different conditions.

> 训练之后,对模型进行全面的评估和测试,确保它在不同条件下表现稳定。

Finally, you deploy your model into the real world and monitor and maintain it based on new insights and feedback.

> 最后,将模型部署到现实世界,并根据新的洞见和反馈对其进行监控和维护。

Now that you know what to expect, the sections below cover each step in detail.

> 既然你已经知道了会发生什么,下面的章节将详细介绍每一步。

Step 1: Defining Your Project's Goals

> 第1步:确定项目目标

The first step in any computer vision project is clearly defining the problem you're trying to solve. Knowing the end goal helps you start to build a solution. This is especially true when it comes to computer vision because your project's objective will directly affect which computer vision task you need to focus on.

> 任何计算机视觉项目的第一步都是明确界定你要解决的问题。了解最终目标有助于你着手构建解决方案。对计算机视觉而言尤其如此,因为项目目标将直接影响你需要关注哪种计算机视觉任务。

Here are some examples of project objectives and the computer vision tasks that can be used to reach these objectives:

> 以下是一些项目目标以及可用于实现这些目标的计算机视觉任务示例:

Objective: To develop a system that can monitor and manage the flow of different vehicle types on highways, improving traffic management and safety.

> 目标:开发一个能监控和管理高速公路上不同类型车辆流量的系统,改善交通管理和安全。

Computer Vision Task: Object detection is ideal for traffic monitoring because it efficiently locates and identifies multiple vehicles. It is less computationally demanding than image segmentation, which provides unnecessary detail for this task, ensuring faster, real-time analysis.

> 计算机视觉任务:目标检测非常适合交通监控,因为它能高效地定位并识别多辆车。它对计算量的要求低于图像分割,而图像分割对这项任务来说提供了不必要的细节,因此目标检测能确保更快的实时分析。

Objective: To develop a tool that assists radiologists by providing precise, pixel-level outlines of tumors in medical imaging scans.

> 目标:开发一个工具,通过在医学影像扫描中提供精确的像素级肿瘤轮廓来协助放射科医生。

Computer Vision Task: Image segmentation is suitable for medical imaging because it provides accurate and detailed boundaries of tumors that are crucial for assessing size, shape, and treatment planning.

> 计算机视觉任务:图像分割适用于医学影像,因为它能提供准确而详细的肿瘤边界,这对评估肿瘤大小、形状和制定治疗方案至关重要。

Objective: To create a digital system that categorizes various documents (e.g., invoices, receipts, legal paperwork) to improve organizational efficiency and document retrieval.

> 目标:创建一个数字系统,对各类文件(如发票、收据、法律文书)进行分类,以提高组织效率和文件检索能力。

Computer Vision Task: Image classification is ideal here as it handles one document at a time, without needing to consider the document's position in the image. This approach simplifies and accelerates the sorting process.

> 计算机视觉任务:图像分类在这里非常理想,因为它一次处理一份文件,无需考虑文件在图像中的位置。这种方法简化并加快了分类过程。

Selecting the Right Model and Training Approach

> 选择合适的模型和训练方式

After understanding the project objective and suitable computer vision tasks, an essential part of defining the project goal is selecting the right model and training approach.

> 在了解了项目目标和合适的计算机视觉任务之后,确定项目目标的一个重要部分是选择合适的模型和训练方式。

Depending on the objective, you might choose to select the model first or after seeing what data you are able to collect in Step 2. For example, suppose your project is highly dependent on the availability of specific types of data. In that case, it may be more practical to gather and analyze the data first before selecting a model. On the other hand, if you have a clear understanding of the model requirements, you can choose the model first and then collect data that fits those specifications.

> 根据目标不同,你可以先选择模型,也可以在看到第2步中能收集到哪些数据之后再选。例如,假设你的项目高度依赖特定类型数据的可得性,那么先收集和分析数据、再选择模型可能更实际。另一方面,如果你对模型要求有清晰的了解,可以先选模型,再收集符合这些规格的数据。

Choosing between training from scratch or using transfer learning affects how you prepare your data. Training from scratch requires a diverse dataset to build the model's understanding from the ground up. Transfer learning, on the other hand, allows you to use a pretrained model and adapt it with a smaller, more specific dataset. Also, choosing a specific model to train will determine how you need to prepare your data, such as resizing images or adding annotations, according to the model's specific requirements.

> 在从头训练和使用迁移学习之间做选择,会影响你准备数据的方式。从头训练需要多样化的数据集,从零开始建立模型的理解能力。而迁移学习则允许你使用预训练模型,并用较小、更具体的数据集对其进行调整。此外,选择训练哪个具体模型,也将决定你需要如何准备数据,例如根据模型的具体要求调整图像大小或添加标注。

Consider deployment when choosing a model

> 选择模型时要考虑部署

Consider a model's deployment target to ensure compatibility and performance. For example, lightweight models are ideal for edge computing thanks to their efficiency on resource-constrained devices.

> 要考虑模型的部署目标,以确保兼容性和性能。例如,轻量级模型在资源受限的设备上效率高,因此非常适合边缘计算。

To learn more, read our guide on defining your project's goals and selecting the right model.

> 想了解更多,请阅读我们关于确定项目目标和选择合适模型的指南。

Before getting into the hands-on work of a computer vision project, it's important to have a clear understanding of these details. Double-check that you've considered the following before moving on to Step 2:

> 在着手计算机视觉项目的实际工作之前,清楚理解这些细节很重要。在进入第2步之前,请再次确认你已考虑以下内容:

Clearly define the problem you're trying to solve.

> 明确界定你要解决的问题。

Determine the end goal of your project.

> 确定项目的最终目标。

Identify the specific computer vision task needed (e.g., object detection, image classification, image segmentation).

> 确定所需的具体计算机视觉任务(如目标检测、图像分类、图像分割)。

Decide whether to train a model from scratch or use transfer learning.

> 决定是从头训练模型还是使用迁移学习。

Select the appropriate model for your task and deployment needs.

> 根据任务和部署需求选择合适的模型。

Step 2: Data Collection and Data Annotation

> 第2步:数据收集与数据标注

The quality of your computer vision models depends on the quality of your dataset. You can either collect images from the internet, take your own pictures, or use pre-existing datasets. Useful sources of public datasets include Google Dataset Search Engine, UC Irvine Machine Learning Repository, and Kaggle Datasets.

> 计算机视觉模型的质量取决于数据集的质量。你可以从互联网上收集图像、自己拍照,或使用现有数据集。有用的公共数据集来源包括Google数据集搜索引擎、加州大学尔湾分校机器学习资料库和Kaggle数据集。

Some libraries, like Ultralytics, provide built-in support for various datasets, making it easier to get started with high-quality data. These libraries often include utilities for downloading and loading popular datasets, which can save you a lot of time and effort in the initial stages of your project.

> 一些库(如Ultralytics)为各种数据集提供内置支持,让你更容易上手高质量数据。这些库通常包含用于下载和加载常用数据集的工具,可在项目初期为你节省大量时间和精力。

However, if you choose to collect images or take your own pictures, you'll need to annotate your data. Data annotation is the process of labeling your data to impart knowledge to your model. The type of data annotation you'll work with depends on your specific computer vision technique. Here are some examples:

> 不过,如果你选择自己收集图像或拍照,就需要对数据进行标注。数据标注是给数据打标签,以便向模型传授知识的过程。你要进行的数据标注类型取决于你所用的具体计算机视觉技术。以下是一些例子:

Image Classification: You'll label the entire image as a single class.

> 图像分类:你会把整幅图像标注为单一类别。

Object Detection: You'll draw bounding boxes around each object in the image and label each box.

> 目标检测:你会在图像中每个物体周围画出边界框,并给每个框打标签。

Image Segmentation: You'll label each pixel in the image according to the object it belongs to, creating detailed object boundaries.

> 图像分割:你会根据像素所属的物体为图像中的每个像素打标签,从而生成详细的物体边界。

Data collection and annotation can be a time-consuming manual effort. A dedicated annotation tool makes it faster: Ultralytics Platform provides a built-in annotation editor with SAM-powered smart annotation for detection, segmentation, and OBB data, saving labels directly in YOLO format.

> 数据收集和标注可能是一项耗时的手工工作。专用的标注工具可以加快速度:Ultralytics Platform提供内置的标注编辑器,带有基于SAM的智能标注功能,可用于检测、分割和OBB数据,并直接以YOLO格式保存标签。

Step 3: Data Augmentation and Splitting Your Dataset

> 第3步:数据增强与数据集划分

After collecting and annotating your image data, it's important to first split your dataset into training, validation, and test sets before performing data augmentation. Splitting your dataset before augmentation is crucial to test and validate your model on original, unaltered data. It helps accurately assess how well the model generalizes to new, unseen data.

> 在收集并标注完图像数据后,重要的是先将数据集划分为训练集、验证集和测试集,然后再进行数据增强。在增强之前划分数据集,对于在原始、未被改动的数据上测试和验证模型至关重要。这有助于准确评估模型对新的、未见过的数据的泛化能力。

Here's how to split your data:

> 数据划分方法如下:

Training Set: It is the largest portion of your data, typically 70-80% of the total, used to train your model.

> 训练集:这是数据中最大的部分,通常占总量的70-80%,用于训练模型。

Validation Set: Usually around 10-15% of your data; this set is used to tune hyperparameters and validate the model during training, helping to prevent overfitting.

> 验证集:通常占数据的10-15%左右;该集合用于调整超参数并在训练期间验证模型,有助于防止过拟合。

Test Set: The remaining 10-15% of your data is set aside as the test set. It is used to evaluate the model's performance on unseen data after training is complete.

> 测试集:其余10-15%的数据留作测试集。它用于在训练完成后评估模型在未见数据上的表现。

After splitting your data, you can perform data augmentation by applying transformations like rotating, scaling, and flipping images to artificially increase the size of your dataset. Data augmentation makes your model more robust to variations and improves its performance on unseen images.

> 划分数据之后,你可以通过旋转、缩放和翻转图像等变换来进行数据增强,从而人为地增加数据集的规模。数据增强使你的模型对各种变化更加稳健,并提升其在未见图像上的表现。

Libraries like OpenCV, Albumentations, and TensorFlow offer flexible augmentation functions that you can use. Additionally, some libraries, such as Ultralytics, have built-in augmentation settings directly within their model training function, simplifying the process.

> OpenCV、Albumentations和TensorFlow等库提供了灵活的增强函数供你使用。此外,一些库(如Ultralytics)在其模型训练函数中直接内置了增强设置,从而简化了流程。

To understand your data better, you can use tools like Matplotlib or Seaborn to visualize the images and analyze their distribution and characteristics. Visualizing your data helps identify patterns, anomalies, and the effectiveness of your augmentation techniques. The Ultralytics Platform Charts tab can surface many of these insights without any code by automatically generating split distribution, class counts, image-dimension histograms, and annotation-position heatmaps for every uploaded dataset.

> 为了更好地了解你的数据,可以使用Matplotlib或Seaborn等工具将图像可视化,并分析其分布和特征。数据可视化有助于发现模式、异常以及增强技术的效果。Ultralytics Platform的图表选项卡可以自动为每个上传的数据集生成划分分布、类别计数、图像尺寸直方图和标注位置热力图,无需任何代码即可呈现其中许多洞见。

By properly understanding, splitting, and augmenting your data, you can develop a well-trained, validated, and tested model that performs well in real-world applications.

> 通过恰当地理解、划分和增强数据,你可以开发出经过良好训练、验证和测试的模型,使其在实际应用中表现出色。

Step 4: Model Training

> 第4步:模型训练

Once your dataset is ready for training, you can focus on setting up the necessary environment, managing your datasets, and training your model.

> 数据集准备好用于训练后,你就可以专注于搭建必要的环境、管理数据集并训练模型。

First, you'll need to make sure your environment is configured correctly. Typically, this includes the following:

> 首先,你需要确保环境配置正确。通常包括以下内容:

Installing essential libraries and frameworks like TensorFlow, PyTorch, or Ultralytics.

> 安装TensorFlow、PyTorch或Ultralytics等必要的库和框架。

If you are using a GPU, installing libraries like CUDA and cuDNN will help enable GPU acceleration and speed up the training process.

> 如果你使用GPU,安装CUDA和cuDNN等库将有助于启用GPU加速并加快训练过程。

Then, you can load your training and validation datasets into your environment. Normalize and preprocess the data through resizing, format conversion, or augmentation. With your model selected, configure the layers and specify hyperparameters. Compile the model by setting the loss function, optimizer, and performance metrics.

> 然后,你可以把训练和验证数据集加载到环境中。通过调整大小、格式转换或增强来对数据进行归一化和预处理。选定模型后,配置各层并指定超参数。通过设置损失函数、优化器和性能指标来编译模型。

Libraries like Ultralytics simplify the training process. You can start training by feeding data into the model with minimal code. These libraries handle weight adjustments, backpropagation, and validation automatically. They also offer tools to monitor progress and adjust hyperparameters easily. After training, save the model and its weights with a few commands.

> Ultralytics等库简化了训练过程。你只需很少的代码,把数据输入模型即可开始训练。这些库会自动处理权重调整、反向传播和验证。它们还提供工具,方便你监控进度并调整超参数。训练结束后,只需几条命令即可保存模型及其权重。

It's important to keep in mind that proper dataset management is vital for efficient training. Use version control for datasets to track changes and ensure reproducibility. Tools like DVC (Data Version Control) can help manage large datasets.

> 要记住,恰当的数据集管理对高效训练至关重要。对数据集使用版本控制,以追踪变更并确保可复现性。DVC(数据版本控制)等工具可以帮助管理大型数据集。

Step 5: Model Evaluation and Fine-Tuning

> 第5步:模型评估与微调

It's important to assess your model's performance using various metrics and refine it to improve accuracy. Evaluating helps identify areas where the model excels and where it may need improvement. Fine-tuning ensures the model is optimized for the best possible performance.

> 使用各种指标评估模型的性能并加以改进以提高准确率,这一点很重要。评估有助于找出模型的优势所在以及可能需要改进的地方。微调确保模型被优化到可能的最佳性能。

Performance Metrics: Use metrics like accuracy, precision, recall, and F1-score to evaluate your model's performance. These metrics provide insights into how well your model is making predictions.

> 性能指标:使用准确率、精确率、召回率和F1分数等指标来评估模型的性能。这些指标能让你深入了解模型的预测效果。

Hyperparameter Tuning: Adjust hyperparameters to optimize model performance. Techniques like grid search or random search can help find the best hyperparameter values.

> 超参数调优:调整超参数以优化模型性能。网格搜索或随机搜索等技术有助于找到最佳的超参数值。

Fine-Tuning: Make small adjustments to the model architecture or training process to enhance performance. This might involve tweaking learning rates, batch sizes, or other model parameters.

> 微调:对模型架构或训练过程做出小幅调整以提升性能。这可能涉及调整学习率、批量大小或其他模型参数。

For a deeper understanding of model evaluation and fine-tuning techniques, check out our model evaluation insights guide.

> 如需更深入地了解模型评估和微调技术,请查看我们的模型评估洞见指南。

Step 6: Model Testing

> 第6步:模型测试

Model testing confirms your model performs well on completely unseen data, verifying its readiness for deployment. The difference between model testing and model evaluation is that testing focuses on verifying the final model's performance rather than iteratively improving it.

> 模型测试确认你的模型在完全未见过的数据上表现良好,验证其是否已准备好部署。模型测试与模型评估的区别在于,测试侧重于验证最终模型的性能,而不是反复迭代地改进它。

It's important to thoroughly test and debug any common issues that may arise. Test your model on a separate test dataset that was not used during training or validation. This dataset should represent real-world scenarios to ensure the model's performance is consistent and reliable.

> 彻底测试并调试可能出现的各种常见问题很重要。请在一个单独的测试数据集上测试模型,该数据集在训练或验证期间未被使用过。这个数据集应当代表真实场景,以确保模型的性能稳定可靠。

Also, address common problems such as overfitting, underfitting, and data leakage. Use techniques like cross-validation to identify these issues. For comprehensive testing strategies, refer to our model testing guide.

> 同时,要解决过拟合、欠拟合和数据泄漏等常见问题。使用交叉验证等技术来发现这些问题。有关全面的测试策略,请参阅我们的模型测试指南。

Step 7: Model Deployment

> 第7步:模型部署

Once your model has been thoroughly tested, it's time to deploy it. Model deployment involves making your model available for use in a production environment. Here are the steps to deploy a computer vision model:

> 模型经过彻底测试后,就该部署了。模型部署指的是让你的模型可在生产环境中使用。以下是部署计算机视觉模型的步骤:

Setting Up the Environment: Configure the necessary infrastructure for your chosen deployment option, whether it's cloud-based (AWS, Google Cloud, Azure) or edge-based (local devices, IoT).

> 设置环境:为你选定的部署方案配置必要的基础设施,无论是基于云(AWS、Google Cloud、Azure)还是基于边缘(本地设备、物联网)。

Exporting the Model: Export your model to the appropriate format (e.g., ONNX, TensorRT, CoreML for YOLO26) to ensure compatibility with your deployment platform.

> 导出模型:将模型导出为合适的格式(例如针对YOLO26的ONNX、TensorRT、CoreML),以确保与你的部署平台兼容。

Deploying the Model: Deploy the model by setting up APIs or endpoints and integrating it with your application.

> 部署模型:通过设置API或端点并将其与你的应用集成来部署模型。

Ensuring Scalability: Implement load balancers, auto-scaling groups, and monitoring tools to manage resources and handle increasing data and user requests.

> 确保可扩展性:实施负载均衡器、自动扩缩容组和监控工具,以管理资源并应对不断增长的数据和用户请求。

Ultralytics Platform also provides managed deployment endpoints in 42 global regions with scale-to-zero by default, handling infrastructure setup automatically.

> Ultralytics Platform还在全球42个区域提供托管的部署端点,默认支持缩容到零,并自动处理基础设施的搭建。

Step 8: Monitoring, Maintenance, and Documentation

> 第8步:监控、维护与文档

Once your model is deployed, it's important to continuously monitor its performance, maintain it to handle any issues, and document the entire process for future reference and improvements.

> 模型部署后,持续监控其性能、对其进行维护以处理任何问题,并将整个过程记录成文档以供日后参考和改进,这一点很重要。

Monitoring tools can help you track key performance indicators (KPIs) and detect anomalies or drops in accuracy. By monitoring the model, you can be aware of model drift, where the model's performance declines over time due to changes in the input data. Periodically retrain the model with updated data to maintain accuracy and relevance.

> 监控工具可以帮助你追踪关键绩效指标(KPI),并发现异常或准确率下降。通过监控模型,你可以察觉模型漂移,即由于输入数据变化而导致模型性能随时间下降的现象。定期用更新的数据重新训练模型,以保持准确性和相关性。

In addition to monitoring and maintenance, documentation is also key. Thoroughly document the entire process, including model architecture, training procedures, hyperparameters, data preprocessing steps, and any changes made during deployment and maintenance. Good documentation ensures reproducibility and makes future updates or troubleshooting easier. By effectively monitoring, maintaining, and documenting your model, you can ensure it remains accurate, reliable, and easy to manage over its lifecycle.

> 除了监控和维护之外,文档也同样关键。要全面记录整个过程,包括模型架构、训练流程、超参数、数据预处理步骤,以及部署和维护期间所做的任何更改。良好的文档能确保可复现性,并使今后的更新或故障排查更容易。通过有效地监控、维护并记录你的模型,你可以确保它在整个生命周期内保持准确、可靠且易于管理。

Engaging with the Community

> 参与社区

Connecting with a community of computer vision enthusiasts can help you tackle any issues you face while working on your computer vision project with confidence. Here are some ways to learn, troubleshoot, and network effectively.

> 与计算机视觉爱好者社区建立联系,可以帮助你有信心地解决在做计算机视觉项目时遇到的任何问题。以下是一些有效学习、排查问题和建立人脉的方式。

Community Resources

> 社区资源

GitHub Issues: Check out the YOLO26 GitHub repository and use the Issues tab to ask questions, report bugs, and suggest new features. The active community and maintainers are there to help with specific issues.

> GitHub Issues:查看YOLO26的GitHub仓库,并使用Issues选项卡提问、报告漏洞和建议新功能。活跃的社区和维护者会帮助解决具体问题。

Ultralytics Discord Server: Join the Ultralytics Discord server to interact with other users and developers, get support, and share insights.

> Ultralytics Discord服务器:加入Ultralytics的Discord服务器,与其他用户和开发者交流、获得支持并分享见解。

Using these resources will help you overcome challenges and stay updated with the latest trends and best practices in the computer vision community.

> 利用这些资源将帮助你克服挑战,并了解计算机视觉社区的最新趋势和最佳实践。

Next Steps

> 后续步骤

You now have a roadmap for every stage of a computer vision project, from defining goals to monitoring a deployed model. Put it into practice by training your first YOLO model, or dive deeper into any single stage through the guides linked above. To run the full pipeline without writing code, explore the Ultralytics Platform.

> 你现在已经拥有了计算机视觉项目各个阶段的路线图,从确定目标到监控已部署的模型。你可以通过训练你的第一个YOLO模型来付诸实践,或通过上文链接的指南深入了解任何单一阶段。若想无需编写代码就运行完整流程,请探索Ultralytics Platform。

## 生词

| 单词 | 音标 | 词性 | 释义 | 例句 |
|---|---|---|---|---|
| annotate | /ˈænəteɪt/ | v. | 注释;标注 | Researchers annotate each image with a short label. |
| augment | /ɔːɡˈment/ | v. | 增加;扩充 | She took a night job to augment her income. |
| robust | /roʊˈbʌst/ | adj. | 稳健的;强健的 | The company needs a robust plan to survive the crisis. |
| deploy | /dɪˈplɔɪ/ | v. | 部署;调配 | The city will deploy more buses during rush hour. |
| retrieval | /rɪˈtriːvl/ | n. | 检索;取回 | Fast data retrieval saves staff a lot of time. |
| reproducibility | /ˌriːprəˌduːsəˈbɪləti/ | n. | 可复现性 | Reproducibility is essential for reliable scientific research. |
| iteratively | /ˈɪtərətɪvli/ | adv. | 迭代地;反复地 | The team improved the design iteratively over several months. |
| impart | /ɪmˈpɑːrt/ | v. | 传授;赋予 | Good teachers impart knowledge and inspire curiosity. |
| scalability | /ˌskeɪləˈbɪləti/ | n. | 可扩展性 | Scalability is vital when a service gains millions of users. |
| unaltered | /ʌnˈɔːltərd/ | adj. | 未改变的 | The ancient village has remained largely unaltered for centuries. |
| refine | /rɪˈfaɪn/ | v. | 改进;精炼 | Scientists continue to refine their methods. |
| optimize | /ˈɑːptəmaɪz/ | v. | 优化 | Companies optimize their websites to attract more visitors. |
| thoroughly | /ˈθɜroʊli/ | adv. | 彻底地;全面地 | After training, you thoroughly evaluate and test your model to make sure it performs consistently under different conditions. |
| monitor | /ˈmɑːnɪtər/ | v. | 监控;持续跟踪(模型运行状况) | Finally, you deploy your model into the real world and monitor and maintain it based on new insights and feedback. |
| radiologist | /ˌreɪdiˈɑlədʒɪst/ | n. | 放射科医生;影像科医师 | Objective: To develop a tool that assists radiologists by providing precise, pixel-level outlines of tumors in medical imaging scans. |
| tumor | /ˈtuːmɚ/ | n. | 肿瘤 | Objective: To develop a tool that assists radiologists by providing precise, pixel-level outlines of tumors in medical imaging scans. |
| objective | /əbˈdʒɛktɪv/ | n. | 目标;目的 | This is especially true when it comes to computer vision because your project's objective will directly affect which computer vision task you need to focus on. |
| from scratch | /frʌm skrætʃ/ | phrase | 从零开始;从头开始 | Choosing between training from scratch or using transfer learning affects how you prepare your data. |
| built-in | /ˌbɪltˈɪn/ | adj. | 内置的;自带的 | Some libraries, like Ultralytics, provide built-in support for various datasets, making it easier to get started with high-quality data. |
| crucial | /ˈkruːʃəl/ | adj. | 至关重要的,关键的 | Computer Vision Task: Image segmentation is suitable for medical imaging because it provides accurate and detailed boundaries of tumors that are crucial for assessing size, shape, and treatment planning. |
| accurately | /ˈækjərətli/ | adv. | 准确地,精确地 | Then, you collect and accurately label the images that will help train your model. |
| generalize | /ˈdʒɛnrəˌlaɪz/ | v. | 泛化;推广适用于(新数据) | It helps accurately assess how well the model generalizes to new, unseen data. |
| vital | /ˈvaɪtəl/ | adj. | 至关重要的;必不可少的 | It's important to keep in mind that proper dataset management is vital for efficient training. |
| readiness | /ˈrɛdinəs/ | n. | 就绪状态;准备就绪的程度 | Step 6: Model Testing

Model testing confirms your model performs well on completely unseen data, verifying its readiness for deployment. |
| overfitting | /ˌoʊvərˈfɪtɪŋ/ | n. | 过拟合(模型过度贴合训练数据,导致对新数据泛化能力差) | Validation Set: Usually around 10-15% of your data; this set is used to tune hyperparameters and validate the model during training, helping to prevent overfitting. |
| cross-validation | /ˌkrɔs ˌvælɪˈdeɪʃən/ | n. | 交叉验证(一种通过将数据多次划分为训练集和验证集来评估模型性能、发现过拟合等问题的方法) | Use techniques like cross-validation to identify these issues. |
| drift | /drɪft/ | n. | 漂移;(模型)性能随数据变化而逐渐退化 | By monitoring the model, you can be aware of model drift, where the model's performance declines over time due to changes in the input data. |
| periodically | /ˌpɪriˈɑdɪkli/ | adv. | 定期地;周期性地 | Periodically retrain the model with updated data to maintain accuracy and relevance. |
| enthusiast | /ɪnˈθuziˌæst/ | n. | 爱好者;热衷者 | Engaging with the Community

Connecting with a community of computer vision enthusiasts can help you tackle any issues you face while working on your computer vision project with confidence. |
| troubleshoot | /ˈtrʌbəlˌʃut/ | v. | 排查并解决故障;故障排除 | Good documentation ensures reproducibility and makes future updates or troubleshooting easier. |
| Discord | /ˈdɪskɔːrd/ | n. | Discord(一款即时通讯与社区聊天平台) | Ultralytics Discord Server: Join the Ultralytics Discord server to interact with other users and developers, get support, and share insights. |
| roadmap | /ˈroʊdmæp/ | n. | 路线图;行动指南 | Next Steps

You now have a roadmap for every stage of a computer vision project, from defining goals to monitoring a deployed model. |

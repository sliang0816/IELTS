# ByteTrack:多目标跟踪算法

- 导入日期：2026-10-29
- 类型：粘贴 / 原文

## 原文 / 译文

ByteTrack is a fast, open-source multi-object tracking (MOT) algorithm that tracks objects in video by associating almost every detection box rather than only high-confidence ones.

> ByteTrack 是一种快速、开源的多目标跟踪(MOT)算法。它通过关联几乎所有的检测框(而不是只关联高置信度的检测框)来跟踪视频中的物体。[1] [2]

How It Works (Two-Stage Association)

> 工作原理(两阶段关联)

• Stage 1 (High-Confidence Matching): It matches high-score detection boxes to existing tracklets using the Hungarian algorithm and Intersection over Union (IoU).
• Stage 2 (Low-Confidence Recovery): It takes the remaining unmatched tracklets and matches them against low-score detection boxes (such as occluded or blurry objects) using a lower IoU threshold.
• Noise Filtering: Low-score boxes that fail to match any active tracklet are treated as background noise and discarded.
• Motion Prediction: It relies on a Kalman filter to forecast object positions and handle short-term occlusions without heavy appearance-based ReID (Re-identification) models.

> • 第一阶段(高置信度匹配):它使用匈牙利算法和交并比(IoU),将高分检测框与现有的轨迹片段进行匹配。[1] [2]
> • 第二阶段(低置信度恢复):它取出剩余未匹配的轨迹片段,使用更低的 IoU 阈值,将它们与低分检测框(例如被遮挡或模糊的物体)进行匹配。[1] [2] [3]
> • 噪声过滤:未能与任何活跃轨迹片段匹配的低分检测框会被视为背景噪声并被丢弃。[1] [2]
> • 运动预测:它依靠卡尔曼滤波器来预测物体位置,并处理短时间的遮挡,而无需依赖庞大的、基于外观的重识别(ReID)模型。[1] [2]

Key Features & Benefits

> 主要特点与优势

• Reduced Fragmented Tracks: Retaining low-score boxes significantly lowers false negatives and ID switches during heavy occlusions.
• High Speed: It runs in real time (e.g., 30 FPS on a single GPU for MOT17) because it uses simple motion and box overlap instead of complex neural network embeddings.
• Detector Agnostic: It pairs easily with modern object detectors like YOLO (such as YOLOv11) in frameworks like Roboflow Supervision or Ultralytics.
• Benchmarks: It achieved strong scores on tracking benchmarks like MOT17 (80.3 MOTA, 77.3 IDF1) and MOT20.
If you want to use ByteTrack, let me know:
• What object detector you are using (e.g., YOLOv8, YOLOv11, RT-DETR)
• What kind of video or application you are tracking (sports, traffic, people counting, etc.)
I can share a quick Python code snippet or setup guide for your workflow.

> • 减少碎片化轨迹:保留低分检测框可显著降低漏检以及在严重遮挡期间发生的 ID 切换。[1] [2] [3]
> • 速度快:它可以实时运行(例如在 MOT17 上,单个 GPU 可达 30 帧/秒),因为它使用简单的运动信息和检测框重叠度,而不是复杂的神经网络嵌入。[1] [2]
> • 与检测器无关:它可以很方便地与 YOLO(如 YOLOv11)等现代目标检测器搭配,并可用于 Roboflow Supervision 或 Ultralytics 等框架。[1] [2] [3]
> • 基准测试:它在 MOT17(80.3 MOTA,77.3 IDF1)和 MOT20 等跟踪基准测试中取得了很好的成绩。[1]
> 如果你想使用 ByteTrack,请告诉我:
> • 你使用的是哪种目标检测器(例如 YOLOv8、YOLOv11、RT-DETR)
> • 你要跟踪的是哪种视频或应用场景(体育、交通、人数统计等)
> 我可以为你的工作流程提供一小段 Python 代码示例或配置指南。

## 生词

| 单词 | 音标 | 词性 | 释义 | 例句 |
|---|---|---|---|---|
| associate | /əˈsoʊʃieɪt/ | v. | 关联;联系 | Many people associate this city with fashion. |
| occluded | /əˈkluːdɪd/ | adj. | 被遮挡的;被堵塞的 | The view of the lake was occluded by tall trees. |
| threshold | /ˈθreʃhoʊld/ | n. | 阈值;门槛 | The pain threshold varies from person to person. |
| discard | /dɪˈskɑːrd/ | v. | 丢弃;抛弃 | Researchers discarded the unreliable data. |
| forecast | /ˈfɔːrkæst/ | v. | 预测;预报 | Experts forecast a rise in global temperatures. |
| rely on | /rɪˈlaɪ ɑːn/ | v. | 依靠;依赖 | Many islands rely on tourism for income. |
| fragmented | /ˈfræɡmentɪd/ | adj. | 碎片化的;不完整的 | The fragmented habitat threatens wildlife. |
| retain | /rɪˈteɪn/ | v. | 保留;保持 | The company aims to retain its best employees. |
| significantly | /sɪɡˈnɪfɪkəntli/ | adv. | 显著地;相当大地 | Prices have risen significantly this year. |
| overlap | /ˈoʊvərlæp/ | n. | 重叠;交叠 | There is some overlap between the two courses. |
| embedding | /ɪmˈbedɪŋ/ | n. | 嵌入;嵌入表示 | Word embedding helps computers understand language. |
| agnostic | /æɡˈnɑːstɪk/ | adj. | 不受限的;与…无关的 | The software is platform agnostic and runs anywhere. |
| benchmark | /ˈbentʃmɑːrk/ | n. | 基准;参照标准 | The test serves as a benchmark for student progress. |
| achieve | /əˈtʃiːv/ | v. | 取得;实现 | She achieved excellent results in the exam. |
| application | /ˌæplɪˈkeɪʃn/ | n. | 应用;用途 | The technology has many practical applications. |
| blurry | /ˈblɝri/ | adj. | 模糊的(指图像中目标因运动或失焦而不清晰) | • Stage 2 (Low-Confidence Recovery): It takes the remaining unmatched tracklets and matches them against low-score detection boxes (such as occluded or blurry objects) using a lower IoU threshold. |
| occlusion | /əˈkluːʒən/ | n. | 遮挡(目标被其他物体部分或完全挡住而暂时不可见) | • Motion Prediction: It relies on a Kalman filter to forecast object positions and handle short-term occlusions without heavy appearance-based ReID (Re-identification) models. |

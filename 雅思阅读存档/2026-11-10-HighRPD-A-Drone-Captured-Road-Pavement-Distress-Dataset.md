# HighRPD: A Drone-Captured Road Pavement Distress Dataset

- 导入日期：2026-11-10
- 类型：粘贴 / 原文

## 原文 / 译文

In order to meet the data needs for road pavement distress detection, we have created a standardized dataset road pavement distress named HighRPD, which consists of road pavement distress images captured from a drone perspective. This dataset maintains a uniform image resolution of 640x640 pixels, in alignment with the test dataset specifications for the YOLO v8 model. Meanwhile, informed by the prevalence of road pavement distress, the dataset HighRPD specifically targets road pavement distress classified into three fundamental categories: line, block, and pit. We utilized the Labelbox platform in combination with DarkLabel for constructing our dataset. In summary, a total of 11,696 road pavement images were successfully labeled, including 12,365 line annotations, 8,239 block annotations, and 1,412 pit annotations.

> HighRPD:无人机拍摄的路面病害数据集

The HighRPD dataset comprises two subfolders: one named 'images' and the other 'labels'. The 'images' folder contains pictures sized 640x640 pixels in JPG format, while the 'labels' folder contains txt files with labels formatted in the YOLO style. Each object is represented by a single line, formatted as 'class center_x center_y width height'. There are three classes: class 0 for lines, class 1 for blocks, and class 2 for pits. The coordinates (x_center, y_center, width, height) are normalized by dividing x_center and width by the image width, and y_center and height by the image height.

## 生词

| 单词 | 音标 | 词性 | 释义 | 例句 |
|---|---|---|---|---|
| pavement | /ˈpeɪvmənt/ | n. | 路面;人行道 | The pavement was damaged by heavy trucks. |
| distress | /dɪˈstrɛs/ | n. | (路面)病害;痛苦 | Cracks are a common sign of pavement distress. |
| standardized | /ˈstændərdaɪzd/ | adj. | 标准化的 | Standardized tests allow fair comparison. |
| uniform | /ˈjunɪfɔrm/ | adj. | 统一的,一致的 | The images have a uniform size. |
| resolution | /ˌrɛzəˈluʃən/ | n. | 分辨率;决议 | The camera has a high resolution. |
| alignment | /əˈlaɪnmənt/ | n. | 一致;对齐 | The policy is in alignment with our goals. |
| specification | /ˌspɛsəfəˈkeɪʃən/ | n. | 规格;详细说明 | The product meets the required specifications. |
| prevalence | /ˈprɛvələns/ | n. | 普遍性;流行程度 | The prevalence of obesity is rising. |
| fundamental | /ˌfʌndəˈmɛntl/ | adj. | 基本的;根本的 | Honesty is fundamental to trust. |
| utilize | /ˈjutəlaɪz/ | v. | 利用 | Farmers utilize drones to monitor crops. |
| annotation | /ˌænəˈteɪʃən/ | n. | 标注;注释 | Each image needs careful annotation. |
| comprise | /kəmˈpraɪz/ | v. | 包含;由…组成 | The dataset comprises two folders. |
| normalize | /ˈnɔrməlaɪz/ | v. | 归一化;使标准化 | Researchers normalize the data before analysis. |
| coordinate | /koʊˈɔrdɪnət/ | n. | 坐标 | The map gives the exact coordinates of the site. |
| drone | /droʊn/ | n. | 无人机 | In order to meet the data needs for road pavement distress detection, we have created a standardized dataset road pavement distress named HighRPD, which consists of road pavement distress images captured from a drone perspective. |
| pit | /pɪt/ | n. | 坑洞(路面凹坑类病害) | Meanwhile, informed by the prevalence of road pavement distress, the dataset HighRPD specifically targets road pavement distress classified into three fundamental categories: line, block, and pit. |
| block | /blɑk/ | n. | 块状(裂缝);块裂 | Meanwhile, informed by the prevalence of road pavement distress, the dataset HighRPD specifically targets road pavement distress classified into three fundamental categories: line, block, and pit. |
| line | /laɪn/ | n. | 线状(裂缝);线形病害 | Meanwhile, informed by the prevalence of road pavement distress, the dataset HighRPD specifically targets road pavement distress classified into three fundamental categories: line, block, and pit. |

### Hey there 👋

### Welcome to my Github
I am Jakob Michel Stock, a passionate researcher in the field of artificial neural network analysis and optimization.
Currently I am doing research on runtime and scalability prediction of convolutional neural networks at TU Darmstadt in the Parallel Programming department of Prof. Felix Wolf.

<p align = "center">
<img src = "deep learning gif.gif">
</p>

🌱 My set goal for 2023 is to join the Scalable Parallel Computing Laboratory of Prof. Torsten Hoefler at ETH Zurich and tackle new challenges in my research in deep learning model optimization.

Make yourself at home and see what I'm working on!

---
# Low-Overhead Latency Predictor
**(August 2021 - Present)**

We found that prediction models based on a combination of activations, FLOPs, and input sizes provide accurate prediction of latency and require little time to learn. They are easy to use, and take runtime implementations into account. Based on these findings, we developed a **latency predictor based on low-overhead profiling using micro-benchmarks** to minimize the performance modeling overhead.

---
# DNN analyzer 
**(January 2021 - August 2021)**

Deep neural networks often consume a lot of computating power and memory, making them quite challenging to be deployed on edge devices.
Our **lightweight neural network analyzer based on PyTorch** predicts the computational requirements of a given DNN.

Check out the repo for more details! https://github.com/TUD-UCB-Boda/dnn_analyzer

## Example

MobileNet-V2 analyzed with our dnn analyzer:

```python
from dnn_analyzer import model_analysis
from torchvision import models

model = models.mobilenet_v2()
model_analysis.ModelAnalyse(model, (3, 224, 224))
```
output:
```bash
+---------------+--------------+-----------------+------------------+----------------+------------------+---------------+---------------+
| module name   |   parameters |   mem read (MB) |   mem write (MB) |   storage (MB) |   inference (MB) |   MACs (Mega) | duration[%]   |
|---------------+--------------+-----------------+------------------+----------------+------------------+---------------+---------------|
| Conv2d        |          864 |           0.578 |            1.531 |          0.003 |            1.531 |         2.71  | 1.37 %        |
| BatchNorm2d   |           64 |           1.531 |            1.531 |          0     |            1.531 |         0.803 | 0.64 %        |
| ReLU6         |            0 |           1.531 |            1.531 |          0     |            1.531 |         0.401 | 0.66 %        |
| Conv2d        |          288 |           1.532 |            1.531 |          0.001 |            1.531 |         3.613 | 0.79 %        |
| BatchNorm2d   |           64 |           1.531 |            1.531 |          0     |            1.531 |         0.803 | 0.59 %        |
| ReLU6         |            0 |           1.531 |            1.531 |          0     |            1.531 |         0.401 | 0.46 %        |
| Conv2d        |          512 |           1.533 |            0.766 |          0.002 |            0.766 |         6.423 | 0.81 %        |
(... shortened to make the doc more readable ...)
| ReLU6         |            0 |           0.179 |            0.179 |          0     |            0.179 |         0.047 | 0.81 %        |
| Conv2d        |       307200 |           1.351 |            0.06  |          1.172 |            0.06  |        15.053 | 0.81 %        |
| BatchNorm2d   |          640 |           0.062 |            0.06  |          0.002 |            0.06  |         0.031 | 0.76 %        |
| Conv2d        |       409600 |           1.622 |            0.239 |          1.562 |            0.239 |        20.07  | 0.81 %        |
| BatchNorm2d   |         2560 |           0.249 |            0.239 |          0.01  |            0.239 |         0.125 | 0.81 %        |
| ReLU6         |            0 |           0.239 |            0.239 |          0     |            0.239 |         0.063 | 0.43 %        |
| Dropout       |            0 |           0     |            0     |          0     |            0.005 |         0     | 0.53 %        |
| Linear        |      1281000 |           4.887 |            0.004 |          4.887 |            0.004 |         1.28  | 0.66 %        |
+---------------+--------------+-----------------+------------------+----------------+------------------+---------------+---------------+
Total Storage:  13.37 MB
Total Parameters:  3504872
Total inference memory:  74.25 MB
Total number of Macs:  308.87 MMAC
Total Memory Read + Write:  162.19 MB
```


---

# That's it!

Thank you for your time! 

📫 Feel free to reach me: jakobstock@web.de

<a href="https://www.linkedin.com/in/jakob-stock-220127217/">
  <img align="left" alt="Jakob's LinkdeIN" width="30px" src="linkedin.png" />
</a>

<!---
Jeykobz/Jeykobz is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

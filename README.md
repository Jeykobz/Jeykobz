### Hey there 👋

### Welcome to my Github
I am Jakob Michel Stock, a passionate researcher in the field of artificial neural network analysis and optimization.
Currently I am doing research on runtime and scalability prediction of convolutional neural networks at TU Darmstadt in the Parallel Programming department of Prof. Felix Wolf.

<p align = "center">
<img src = "images/deep learning gif (1).gif">
</p>

🌱 My set goal for 2023 is to join the [Scalable Parallel Computing Laboratory of Prof. Torsten Hoefler](http://spcl.inf.ethz.ch/) at ETH Zurich and tackle new challenges in my research in deep learning model optimization.

Make yourself at home and see what I'm working on!

---
# Low-Overhead CNN Latency Predictor
**(August 2021 - Present)**

We found that prediction models based on a combination of activations, FLOPs, and input sizes provide accurate prediction of latency and require little time to learn. They are easy to use, and take runtime implementations into account. Based on these findings, we developed a **latency predictor based on low-overhead profiling using micro-benchmarks** to minimize the performance modeling overhead.

* Our approach is related to [PALEO: A PERFORMANCE MODEL FOR DEEP NEURAL NETWORKS](https://openreview.net/pdf?id=SyVVJ85lg) by Hang Qi et al. but achieves better accuracy by using machine learning methods that also consider runtime behaviors of various operators
* The training of our model is more than **1500% more time efficient** than [Microsoft's nn-meter](https://github.com/microsoft/nn-Meter) latency predictor (5-15 minutes vs 1-4 days)
* Learning our model only requires benchmarking **100 samples instead of over a billion**, making our approach **more energy efficient** than Microsoft's

For more preliminary information, see the Repo! https://github.com/Jeykobz/dnn-latency-predictor

## Example
In the following example we learn a latency predictor for the Nvidia A100 80GB GPU.<br />

Initially, our model collects a training data set by running our developed micro benchmarking tool.<br />
By using machine learning methods, our algorithm automatically trains regression models based on the collected micro training dataset.

<p align = "center">
<img src = "images/CMD output image.png">
</p>

The following graph shows the performance of the learned latency prediction model for the Nvidia A100 80GB GPU.<br /> 
Each point represents a sample from the collected test data set, which contains a total of over 17000 data points. The purple line indicates the predicted latencies.

<p align = "center">
<img src = "images/A100 results.svg">
</p>

Our prediction model for the Nvidia A100 GPU achieves **low median errors** of 
* **20.87%** in the low latency range (<2ms) 
* **9.46%** in the high latency range (>2ms)

as well as a high **correlation of 0.98** between the actual and the predicted latency and a **R-squared value of 0.96**.

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

<a href="https://www.linkedin.com/in/jakob-michel-stock-220127217/">
  <img align="left" alt="Jakob's LinkdeIN" width="30px" src="images/linkedin.png" />
</a>

<!---
Jeykobz/Jeykobz is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

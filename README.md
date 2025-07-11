# Brain Tumor Classification

<div align="justify"> 
Brain tumors pose a significant threat to human health, often leading to severe neurological damage or even fatal outcomes if not diagnosed early. Traditional diagnostic methods rely heavily on manual analysis of MRI (Magnetic Resonance Imaging) scans by radiologists, a process that is time-consuming, susceptible to human error, and inefficient at scale—especially when subtle abnormalities occur in only a few image slices.
</div><br>
<div align="justify"> 
This project presents a deep learning-based approach to automated brain tumor classification, leveraging the strengths of Convolutional Neural Networks (CNN), InceptionV3, and Xception architectures. Each model is trained to classify MRI images into three categories: Glioma, Meningioma, and No Tumor.
</div><br>
<div align="justify"> 
To enhance model performance and reliability, the system incorporates key preprocessing steps such as grayscale conversion, noise reduction using median filters, morphological operations, and data augmentation. These steps ensure high-quality input for training and enable the models to generalize effectively across various image patterns.
</div><br>
<div align="justify"> 
The use of MRI scans, which offer high contrast and detailed visualization of soft tissues without ionizing radiation, makes this system both safe and clinically applicable. By automating tumor classification with deep learning, this project aims to support radiologists in improving diagnostic accuracy, reducing workload, and enabling faster, early detection in critical cases. </div><br> 

## Setup
<h3>
<div>
<img src="img/env.png"; width=20> <b>Environment</b>
</div>
</h3>

*Note - The above codes are written using Python virtual environment version **3.12.1** and supports the latest Python versions. However, lower Python versions may offer more stability compared to the latest ones. Below setup will focus Windows system. And commands to setup may vary for macOS or Linux.*



<div> 1. Create a python virtual environment using -

```bash
# Path to installation of particular version of python  may vary
# I have installed more than one version of python in pyver directory
# Refer the resources section, for youtube video to install multiple versions of python
C:\Users\<username>\pyver\py3121\python -m venv brainenv
```
</div>


<div>2. Activate the virtual environment using -

```bash
brainenv/Scripts/activate
```
</div>

<div> 3. Install python packages using - 

```bash
pip install -r requirements.txt
```
</div>

<div> 4. Jupyter Notebook Configuration -

```bash
ipython kernel install --user --name=myenv
python -m ipykernel install --user --name=myenv
```
</div>

<div> 5. For bash based cell execution inside Jupyter (Optional) -

```bash
pip install bash_kernel
python -m bash_kernel.install
```
</div>

<div> 6. Congratulations! Now the environment is ready for execution -

```bash
jupyter notebook
```
</div>

## Model based approach to extract information about Brain Tumor from MRI scans

1. **Convolutional Neural Network** (CNN) <br> CNNs are specialised neural networks that are used for image recognition and classification tasks. These networks use multiple layers with adjustable filters to process input data through convolution operations, followed by a non-linear activation function. A CNN architecture comprises convolutional, pooling, ReLU (Rectified Linear Unit), and fully connected layers <div><br>**Convolutional Layer**: This layer extracts features from input data by applying trainable filters (kernels). The filters scan small regions of the input image and produce a feature map.</div>  The *mathematical representation* of the convolution process is: <div>G[m, n] = (f * h)[m, n] = ΣjΣk h[j, k]f[m − j, n − k] where f is the input image and h is the kernel</div> <div><br> **ReLU Layer**: ReLU is a non-linear activation function that replaces negative values in the feature map with zero, defined as f(x) = max(0, x).</div> <div><br>**Pooling Layer**: This layer reduces the dimensions of the activation map while preserving essential information. It divides the input image into non-overlapping regions and applies a down-sampling operation, such as max pooling.</div> <div><br>**Fully Connected Layer**: This layer functions as a traditional classifier, using the information generated by the previous layers to provide a final classification output. The CNN output must be flattened before being fed into the fully connected layer.</div>
<div align="center"><img src="img/1.png"></div><br>

2. **Inception V3** <br> The Inception V3 model is a deep learning framework for image classification that builds upon the original Inception V1 (GoogLeNet) model. Inception V3 comprises 42 layers and has a reduced error rate compared to earlier versions. The main enhancements in this model include breaking down convolutions into smaller components, spatial factorisation through asymmetric convolutions, the role of auxiliary classifiers, and optimised grid size reduction <div>**Factorized Convolutions**: This technique reduces the computational load by decreasing the number of parameters in the network.</div><div><br>**Asymmetric Convolutions**: A 3x3 convolution can be substituted with a 1x3 convolution followed by a 3x1 convolution.</div> <div><br>**Auxiliary Classifier**: An auxiliary classifier is a compact CNN integrated between layers during training, with its loss contributing to the overall network loss. In InceptionV3, these classifiers function primarily as regularisers.</div> <div> <br>**Grid Size Reduction**: Grid size reduction is commonly achieved through pooling operations.</div><div align="center"><img src="img/2.png"><br>

3. **Xception**<br> The Xception architecture is a CNN that extends the Inception architecture. The central innovation of Xception is the replacement of traditional convolutional layers with depthwise separable convolutions. <div>*Xception* refines the Inception approach further by decomposing convolutional layers into depthwise separable convolutions, a two-step operation that improves computational efficiency.</div> <div><br>The Xception module has three main parts: the Entry flow, the Middle flow (repeated 8 times), and the Exit flow.</div> <div> <br>The entry flow has two blocks of convolutional layers followed by a ReLU activation. The architecture includes various separable convolutional layers and max pooling layers. Skip connections are also utilised, merging two tensors using the 'ADD' operation.</div><br> <div align="center"><img src="img/3.png"></div>



## Results

| Contribution | Type of classifier | Accuracy | 
| :--: | :--: | :--: |
| Proposed approach | CNN | 0.96 |
| Proposed approach | Inception | 0.99 |
| Proposed approach | Xception | 0.99 |
| Pashaei et al. [28] | CNN | 0.9368 |
| Gumaei et al. [29] | FNN (feedforward neural network) | 0.9423 | 
<br>

<h3>Visualization</h3>
<div align="center"> 
<img src="img/4.png"; alt="Result"; width=700;height=350><br> 
<img src="img/5.png"; alt="Result"; width=900; height=300><br><i> Results of CNN algorithm for Brain MRI classification (a) Accuracy (b) Loss (c) Classification report (d) Confusion Matrix </i> 
</div><br>

<div align="center"> 
<img src="img/6.png"; alt="Result"; width=700;height=350><br> 
<img src="img/7.png"; alt="Result"; width=900; height=300><br><i> Results of Xception algorithm for Brain MRI classification (a) Accuracy (b) Loss (c) Confusion Matrix (d) Classification report  </i> 
</div><br>

<div align="center"> 
<img src="img/8.png"; alt="Result"; width=700;height=350><br> 
<img src="img/9.png"; alt="Result"; width=900; height=300><br><i> Results of InceptionV3 algorithm for Brain MRI classification (a) Accuracy (b) Loss (c) Confusion Matrix (d) Classification report </i> 
</div><br>

## References
<ol>
<li>S. Ajikumar, Dr. A. Jayachandran Early Diagnosis of Primary Tumor in Brain MRI 
Images using wavelet as the input of AdaBoost classifier 2014 International Conference 
on Contemporary Computing and Informatics (IC3I) </li>
<li>Carlos Arizmendi, Alfredo Vellido, Enrique Romero Binary Classification of Brain 
Tumours Using a Discrete Wavelet Transform and Energy Criteria 978-1-4244-9485 
9/11/$ 26.00 2011 IEEE </li>
<li>Dipali M. Joshi, Dr. N. K. Rana, Classification of Brain Cancer Using Artificial Neural 
Network, 2010 2nd International Conference on Electronic Computer Technology 
(ICECT 2010) IEEE </li>
<li>Salim Lahmiri and Mounir Boukadoum, Classification of Brain MRI using the LH and 
HL Wavelet Transform Sub-bands 978-1-4244-9474-3/11/$ 26.00 2011 IEE </li>
<li>Deji Lu, Yu Sun, Suiren Wan, Brain Tumor Classification Using Non-negative and Local 
Non-negative Matrix Factorization 978-1-4799-1027-4/13/$ 31.00 2013 IEEE </li>
<li>Janki Naik, Prof. Sagar Patel. Tumor Detection and Classification using Decision Tree in 
Brain MRI, Tumor Detection and Classification using Decision Tree in Brain MRI | ISSN: 
2321-9939. </li>
<li>Ahmed KHARRAT, Karim GASMI, Mohamed BEN MESSAOUD, Nacera 
BENAMRANE and Mohamed ABID, A Hybrid Approach for Automatic Classification 
of Brain MRI Using Genetic Algorithm and Support Vector Machine, Leonardo Journal 
of Sciences, Issue 17, July-December 2010, pp. 71-82, ISSN 1583-0233 </li>
<li>Swati, Z.N.K; Zhao, Q.; Kabir, M., Ali, F.; Ali, Z.; Ahmed, S.; and Lu, J. (2019). Brain 
tumor classification for MR images using transfer learning and fine-tuning. Computerized 
Medical Imaging and Graphics, 75, 34-46. </li>
<li>Wasule, V.; and Sonar, P. (2017). Classification of brain MRI using SVM and KNN 
classifier. Third International Conference on Sensing, Signal Processing and Security, 
Chennai, India. 218-223.</li>
<li>Sonavane, R.; and Sonar, P. (2016). Classification and segmentation of brain tumor using 
Adaboost classifier. International Conference on Global Trends in Signal Processing, 
Information Computing, and Communication, Jalgaon, India, 396-403. </li>
<li>Balakumar, B.; Raviraj, P.; and Devi, E.D. (2017). Brain Tumor Classification Using 
Machine Learning Algorithms. Elysium Journal of Engineering Research and 
Management, 4(2), 30-41. </li>
<li>Byale, H.; Lingaraju, G.M.; and Sivasubramanian, S. (2018). Automatic segmentation 
and classification of brain tumors using machine learning techniques. International 
Journal of Applied Engineering Research, 13(14), 11686-11692.  </li>
<li>Badza, M.; and Barjaktarovic, C. (2020). Classification of brain tumors from MRI images 
using a convolutional neural network. Journal of Applied Science, 10(6), 1-13. 14. </li>
<li>Ruba, T.; Tamilselvi, R.; Beham, M.P.; and Aparna N. (2020). Accurate Classification 
and Detection of Brain Cancer Cells in MRI and CT Images using Nano Contrast Agents. 
Journal of Biomedical and Pharmacology, 13(3), 1227-1237.  </li>
<li>Zacharaki E.I.; Wang S.; Chawla S.; Yoo D.S.; Wolf R.; Melhem E.R., and Davatzikos 
C. (2009). Classification of brain tumor type and grade using MRI texture and shape in 
a machine learning scheme. Journal of Magnetic Resonance Medicine, 62(6), 1609-1618.  </li>
<li>Sultan, H.H.; Salem, N.M.; and Walid, A.A. (2019). Multi-Classification of brain tumor 
images using deep neural network. IEEE Access, 7, 69215-69225.  </li>
<li>Deepak, S.; and Ameer, P.M. (2019). Brain tumor classification using deep CNN features 
via transfer learning. Computers in Biology and Medicine, 111, 1-7.  </li>
<li>Ismael, M.R.; and Abdel-Qader, I. (2018). Brain tumor classification via statistical 
features and back-propagation neural network. IEEE International Conference on Electro 
/ Information Technology, Rochester, USA, 252-257. </li>
<li>Sajjad, M.; Khan, S.; Khan, M.; Wu, W.; Ullah, A.; Baik, S.W. (2019). Multi-grade brain 
tumor classification using deep CNN with extensive data augmentation. Journal of 
Computational Science, 30, 174-182. </li>
<li>Talo, M.; Yildirim, O.; Baloglu, U.B.; Aydin, G.; and Acharya, U.R. (2019). 
Convolutional neural networks for multi-class brain disease detection using MRI images. 
Computerized Medical Imaging and Graphics. 78. 1-25.</li>
<li>Kumar, B.A.; and Kumar, P.R. (2019). Classification of MR Brain tumors with deep 
plain and residual feed forward CNNs through transfer learning. International Journal of 
Engineering and Advanced Technology, 8(6), 1758-1763 </li>
<li>Talo, M.; Baloglu U.B.; Yildirim, O.; and Acharya U.R. (2019). Application of deep 
transfer learning for automated brain abnormality classification using MR images. 
Journal of Cognitive Systems Research, 54, 176-188. </li>
<li>A PADMA and R. Sukanesh, "Automatic Classification and Segmentation of Brain 
Tumor in CT Images using Optimal Dominant Gray level Run length Texture Features" 
International Journal of Advanced Computer Science and Applications (IJACSA), 2(10), 
pp. 53- 59, 2011. </li>
<li>R. Y. Vicente, R. R. Tejada, G. J. O. Fernando, R. P. Cimagala, Y. D. Austria and D. C. 
P. Evangelista, "Deep Convolutional Network Tumor Classification System in Brain 
MRI," 2022 IEEE International Conference on Electronics, Computing and 
Communication Technologies (CONECCT), Bangalore, India, 2022, pp. 1-6 </li>
<li>S. Nidaan Khofiya, Y. Nur Fu’adah, N. Kumalasari Caecar Pratiwi, R. Ilmi Naufal and 
A. Deta Pratama, "Brain Tumor Classification Based On MRI Image Processing With 
Alexnet Architecture," 2022 IEEE Asia Pacific Conference on Wireless and Mobile 
(APWiMob), Bandung, Indonesia, 2022, pp. 1-6 </li>
<li>P Gokila Brindha et al 2021 IOP Conf. Ser.: Mater. Sci. Eng. 1055 012115 </li>
<li>Arjun Thakur, Rishab Khandelwal, Ganesh Bhutkar, Rajat Harne and Sankalp Chordia,” 
AI Technique for Classification of Brain Tumor MRI Images for General Physicians,” 
YMER, VOLUME 21 : ISSUE 10 (Oct) – 2021 </li>
<li>Pashaei A, Sajedi H, Jazayeri N. Brain tumor classification via convolutional neural 
network and extreme learning machines. In: 2018 8th international conference on 
computer and knowledge engineering (ICCKE). IEEE; 2018 Oct 25. p. 314–9. </li>
<li>Gumaei A, Hassan MM, Hassan MR, Alelaiwi A, Fortino G. A Hybrid feature extraction 
method with regularized extreme learning machine for brain tumor classification. IEEE 
Access. 2019; 7:36266–73. </li>
</ol>

# Surface Roughness Prediction via Vibration Data with AI Method
#### IoT based surface quality prediction, a project to collect and analyze vibration data in python and use the data to predict for surface quality prediction.
#### vibration data of 100 experiments are stored in folder "clamp" and folder"robot". 
#### file feature extraction-Y (2).ipynb shows the process of extraction of vibration features in time domain and frequency domain.
#### model_mlr_train.ipynb shows the prediction model with multiple linear regression method.
#### model_train_mlp.ipynb shows the prediction model with multilayer perceptron methon.
#### model_train_tree.ipynb shows the prediction model with LightGBM method.
# 1. Abstract
#### When inspecting the quality of machined parts, surface roughness is an essential quality indicator. But due to the limitations of the equipment and economic reasons, it is difficult to measure the surface roughness directly during the machining process by measurement equipment. To monitor the surface quality during the milling process, this project proposed a surface quality prediction model conducted by analyzing a large amount of data from sensors and applying artificial intelligence algorithms (multiple linear regression, tree-based model (LightGBM), artificial neural network. 
#### In this project, experiments under various cutting parameters during the robot-assisted milling process are employed. The statistical data analysis of the result of these machining tests can explore the effect of cutting parameters on surface roughness. Following that, machining process optimization with better surface quality and less vibration can be obtained using prediction models developed using various approaches such as statistical regression and artificial intelligence-based models. The machine learning method and FFT (Fast Fourier Transform) method are applied to extract inconspicuous features from raw vibrational signals during the data processing phase. To optimize the predictive model, the surface roughness prediction models with the combination of different parameters (depth of cut, spindle speed, feed rate, the vibration of the clamp and robot) are built. The experimental equipment used in this research is the KUKA 6-axis milling robot in Incremental Manufacturing Lab, which has more flexibility and more degrees of freedom.
# 2. Experiment
### 1) Design of Experiment

#### spindle speed n (rpm), feed rate fz (f/tooth), and the depth of cut doc (mm) have a more significant effect on machining vibration and machined surface roughness. 
#### By varying the machining parameters, it is possible to obtain a range of vibration amplitudes and surface roughnesses in order to determine the ideal machining parameters for the robot.  Since the maximum spindle speed of the robot can only be 16000, the spindle (n) speed was set to 8000-16000 rpm, increased in increments of 2000, respectively. #### The feed rate fz (feed per tooth) was set at 0.025, 0.05,0.075, and 0.01 (mm/t) at first. Because the measured surface roughness Ra of the tests with 0.025 fz  always more than 15, which means very inferior surface quality. 
#### Finally the feed per tooth fz was set at 0.05, 0.065, 0.075, 0.01 (mm/t). In addition, the linear feed rate of robot vf (mm/min) can be calculated by spindle speed n and feed per tooth based on the formula:  v_f=〖n(spinlde speed)∙f〗_z (feed per tooth)∙z(nummer of tooth). 
#### In this project, various combinations with these three cutting parameters were used for deploying the experiments. Therefore, the following parameter combination can be obtained, as follows:

![C}( 6QBCGPJM9Z88(Z@ZZ 4](https://user-images.githubusercontent.com/73990275/153081549-8e1d84c7-de19-4e82-8f9b-80c7860591ec.png)
### 2) experimental equipment
#### 1) CISS
#### In the experiments, two CISS sensors are mounted respectively on the clamp and robot for measuring their acceleration signals of vibration in the orthogonal directions (X, Y and Z) simultaneously. In addition, these two sensors are linked with an edge device (Raspberry Pi) to transfer the vibrational signal.  
#### 2) surface roughness tester
![J)WH(4QOLNEN0QX{$$CG P6](https://user-images.githubusercontent.com/73990275/153081452-e7b282a7-f799-4caa-a675-3041bea872f9.png)
#### 3) vibration data of 100 experiments are stored in folder "clamp" and folder"robot". 
# 3. Data Mining Process
#### Data mining Process involves 4 main parts, namely data understanding, data preparation, modelling and evaluation.
### 1) Data understanding
#### In the section of data understanding the relationship between the surface roughness with different cutting parameters are analyzed. And the Outliers can be found and deleted.
![J{LCVJYYKV%M61Y PGDD4N2](https://user-images.githubusercontent.com/73990275/153081571-35b65567-5899-4aed-b542-9cf754cc5edd.png)

### 2) Data Preparation
#### The main content of this section is to process the vibrational data. It involves mainly three parts: extracting the valid data during the milling process  from the raw data, extracting the vibrational features in the time domain and in the frequency domain.
![GZ6R_BBLFT}2Z $V)3 GQES](https://user-images.githubusercontent.com/73990275/153284103-58d29614-7785-4c4b-97b0-0f404c086160.png)
### 3) Modeling
![JN)V%O~Q5D0X40C(C NYX C](https://user-images.githubusercontent.com/73990275/153081708-e66d71a7-88f6-4eb2-adde-814196068511.png)
### 4) Evaluation
![Z6GZX H%W ( _6Y2S~T2_ T](https://user-images.githubusercontent.com/73990275/153081774-1deb0453-0d70-4576-a976-25a356a5563c.png)
### 4. Results 
#### comparison of different prediction models with different combination of inputs
![4VF2Z9IETXP87(BUW{WG~(C](https://user-images.githubusercontent.com/73990275/153081899-05e9b62f-8add-42a0-8849-989d0fd791cd.png)
### The best prediction accuracy 
#### It can be found that no matter which features are selected as inputs, the lightGBM always has the best predictive performance.
![5 AQYJ}{JZ69((P`_ 6C](https://user-images.githubusercontent.com/73990275/153081843-3d18a485-185d-4d8a-9a87-0707f6bfbf68.png)


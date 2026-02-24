# MPU6050-library-for-STM32
It is a source code library for MPU6050 that is plug and play with STM32 so you don't have to write code entire code 
MPU6050 STM32 HAL LibraryThis is a lightweight source code library for the MPU6050 6-axis IMU that is designed to be "plug and play" with STM32 microcontrollers.\
It handles the I2C communication, sensor scaling, and startup calibration so you don't have to code the entire driver from scratch Quick Start (STM32CubeIDE)1.\
InitializationAdd the initialization and calibration function inside your 
>[!NOTE]
>main.c file, before the while(1) loop.\
>This will wake up the sensor and establish the base offset values.\
>/* USER CODE BEGIN 2 */\
>MPU6050_Init();\
>/* USER CODE END 2 */\
2.
>[!NOTE]\
>Reading DataAdd the data acquisition and conversion functions inside your\
>while(1) loop to get real-time motion data\
>/* USER CODE BEGIN WHILE */\
>while (1)\
>{\
>    MPU6050_read_data();\
>    data_convert();\
>    HAL_Delay(10);\
>// Adjust loop frequency for your flight computer\
>/* USER CODE END WHILE */\
>}\

Data AccessThe library processes raw values into a true_reading structure using standard units (g-force and degrees per second):\
VariableDescriptionUnit\ 
true_reading.axceloro[0-2] -->3-Axis Accelerometer Data g \
true_reading.gyro[0-2] -->3-Axis Gyroscope Data°/s \
true_reading.temp -->Internal Die Temperature°C\
true_reading.base_value -->Stored Calibration Offsets Raw/Float.

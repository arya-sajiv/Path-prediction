# Path-prediction
Path Prediction using Deep Learning  (LSTM) on GeoLife GPS Trajectories


### Introduction
This project is actually built based on the crucial ability to predict human movement in a wide range of applications including navigation systems, urban planning, traffic management, and location based services. 

Traditional models such as Markov chains and autoregressive methods often fall short in capturing the temporal dependencies and nonlinear patterns found in real-world movement data. In contrast, deep learning models, particularly LSTM networks, offer a powerful alternative due to their capacity to model long-term dependencies in sequential data.

LSTM networks are a powerful tool for modeling sequential data due to their ability to remember long-term dependencies and manage the flow of information. 
This project investigates how an LSTM network can be applied to real GPS trajectories to accurately predict the next location in a user’s path. To develop a predictive model that can be integrated into intelligent transportation systems, providing real-time assistance and optimizing user experiences in smart city ecosystems.

### Dataset:
The GeoLife GPS Trajectories dataset, made publicly available by Microsoft Research Asia, is a rich and comprehensive collection of real-world mobility data. It captures the spatiotemporal movement of 182 users, primarily in Beijing, China, over a period of five years (April 2007 to August 2012). The dataset comprises over 17,000 individual trajectories, totaling more than 1.2 million kilometers and 48,000+ hours of travel. These trajectories represent a diverse range of activities including walking, cycling, driving, and taking public transportation. 

Each user trajectory is recorded as a .plt file, which stores a sequence of timestamped GPS coordinates along with latitude, longitude, altitude, number of seconds since the previous point, and date-time stamps. The dataset is highly granular, with data points recorded at intervals of 1 to 5 seconds, resulting in fine-resolution movement paths. This high sampling rate enables precise modeling of user behavior and movement dynamics.

### Methodology
The methodology of this project involves several stages, starting with data preprocessing. The .plt files are parsed to extract latitude and longitude values along with their corresponding timestamps, which are then combined into a single datetime object for analysis. The extracted coordinates are normalized to a 0 to 1 range using the MinMaxScaler to ensure consistency and improve model performance. Sequences are then created using a sliding window approach, where ten consecutive GPS points are used as input to predict the eleventh point. This transforms the data into a format suitable for training an LSTM model. 

The model architecture consists of an input layer that receives sequences of GPS coordinates, followed by an LSTM layer with sixty-four units that processes the sequence data. A dense output layer then predicts the next GPS coordinate in the sequence. The model is compiled using the mean squared error as the loss function and the Adam optimizer for gradient descent. Training is conducted over twenty epochs with a batch size of thirty-two, and twenty percent of the data is reserved for validation to monitor the model’s generalization performance.

## How to install
Download the GeoLife GPS Trajectories dataset given in the respiratory and give the path to the base_dir code
Example: base_dir = r"C:\Users\nandh\Downloads\archive\Geolife Trajectories 1.3\Data"

Then navigate through the GeoLife dataset directory structure, read GPS trajectory files for each user, and display the first few rows of the data. It is a foundational step for further analysis or processing of the trajectory data.

Set up the necessary libraries for a project that likely involves data processing, normalization, visualization, and building a deep learning model using LSTM networks. Each library plays a crucial role in the workflow, from handling data to training and evaluating the model.

The read_geolife_trajectory function is designed to read a GPS trajectory file, process the data by assigning column names, create a datetime representation of the trajectory points, and return a simplified DataFrame containing only the latitude, longitude, and datetime information. 

Then the code processes GPS trajectory data from the GeoLife dataset for a limited number of users and files. It reads the trajectory files, filters out those with fewer than 20 points, and stores the latitude and longitude information in a list called trajectories. This approach allows for efficient data handling and prepares the data.

Prepare the trajectory data for training a sequence prediction model. It normalizes the latitude and longitude coordinates, creates input sequences of a specified length, and generates corresponding output labels. The resulting arrays X and y are structured appropriately for use in training an LSTM model or other sequence-based machine learning algorithms.

Build a straightforward LSTM neural network to predict the next GPS coordinate in a sequence. The model learns sequential dependencies in the trajectory data, making it useful for tasks such as path prediction using historical GPS points. By using an LSTM layer followed by a dense output layer, the model is trained with mean squared error loss to minimize the difference between predicted and actual coordinates over multiple epochs.

Visually compares the predicted GPS trajectory points from the LSTM model against the actual observed points for a subset of data. By plotting both paths on the same graph after reversing the normalization, you can easily evaluate how well the model predicts future locations based on past trajectories.

Take a predicted GPS point in its scaled form, reverses the scaling to obtain the original latitude and longitude values, and then prints these values. This is useful for interpreting the model's output in a meaningful way, allowing you to see the predicted next location in geographic coordinates.

Evaluate the performance of the model's predictions by calculating and printing the Mean Absolute Error (MAE), Mean Squared Error (MSE), and Root Mean Squared Error (RMSE) for both latitude and longitude. These metrics provide insights into the accuracy of the model's predictions, with lower values indicating better performance.

### Applications
The implications of this project are wide-ranging 
1. Enhanced Navigation Systems 
The LSTM model can improve GPS navigation tools by predicting the user’s future path, allowing for dynamic route adjustments and more accurate Estimated Time of Arrival (ETA) calculations. 
2. Intelligent Traffic Management 
By forecasting vehicle or pedestrian movement, traffic control systems can identify congestion hotspots in advance and reroute traffic proactively to balance road usage. 
3. Smarter Location-Based Services 
Services like personalized advertisements, local alerts, or app notifications can be triggered based on predicted future locations, improving user engagement and service relevance. 
4. Context-Aware Recommendations 
Applications such as food delivery or ride-hailing can use location prediction to suggest timely and relevant options depending on where a user is likely to go. 
5. Urban Planning and Infrastructure Design 
Predicted movement trends can help city planners identify high-traffic zones, optimize public transportation routes, and plan infrastructure expansions based on anticipated user behavior. 
6. Public Transport Optimization 
Transit agencies can use trajectory prediction to monitor passenger flow, adjust service frequency, and improve coverage in underserved areas.

### Results
The trained LSTM model was evaluated using standard metrics such as Mean Absolute Error and Root Mean Squared Error to measure the accuracy of predictions. The results indicate that the model is capable of closely predicting future GPS points, particularly in scenarios involving linear or frequently traveled routes. Visualizations of predicted paths against actual paths reveal a strong correlation, confirming that the model has effectively learned the underlying movement patterns. In more complex or erratic trajectories, the model’s performance slightly declines, highlighting potential areas for improvement. 
To evaluate the effectiveness of the model, we monitored the training process using Mean Squared Error (MSE) as the primary loss metric. The training loss steadily decreased across epochs, indicating that the model was successfully learning spatiotemporal patterns in the GPS data without overfitting.
Additionally, we plotted the predicted vs. actual GPS coordinates. In most sequences, the predicted points followed the true path very closely, confirming the LSTM's ability to learn sequential movement patterns.

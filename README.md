## LOADING AND UNLOADING CHARECTERISTICS OF MATERIALS

 The stress-strain graph of a material is a fundamental tool for understanding how the material respond to mechanical loading and is essential for the design and analysis of engineering structures. Existing method to plot or find the stree-strain graph (or relation) involves preparing a sample of the material and testing in UTM (Universal Testing Machine) or any other sophisticated mmachine. This is resource and time intensive, in order to test one sample, the sample have to be carefully cut or made in a specific shape that can be fit in the machine and then tested. One wrong mistake (in design or composition of the material) causes wastage of time and work. On succesfull testing, we will get a graph, which shows the variation of stress w.r.t strain in loading and unloading phase (which can be linear unlaonding or exponential unloading). The machine shows the stress and strain at different timesteps and also the stress-strain plot of these datapoints.

 Loading and Unloading can be of several kinds, in general, they follow 'Linear' or 'Exponential' plot.

 Linear: Y = a(x) + b, where a, b are coefficients and can be found by observing the stress-strain plot obtained from the above experiment. (fitting the data on a curve fitting software gives us the coefficients)
 Exponential: Y = a*(e^(-bx)) + c, where a, b and c are coefficients and can be found from the stress-strain plot obtained from the above experiment.

Existing approaches requires carefull preparation and testing of the sample to find the loading and unloading charecteristic (graph or plot), which, as dicussed above, is resource and time intensive. With Machine Learning and Neural Network gaining importance in every field, I incorporated ANN (Articficial Neural Network) in our work to find the charecteristic equation(a, b, c values) of the stress-strain plot of the material using its properties ('Loading Plasticity Value','Unloading Plasticity','Coefficient Plasticity Depth','Coefficient Adhesion'). Since this is supervised learning, we extracted some of the data from the SQL database using simple queries and able to get 4,274 samples data. This data is verified by working scholars. 

Data is carefully cleaned for any missing values or outliers in presence of shcolars, and ANN model's are built for the prediction of the charecteristics of the plot. My idea is that, we use one ANN for finding the loading charecteristics (to find the equation in loading phase), and 2 more ANN's to find the Linear unloading and Exponential unloading charecterisitics. We first trained a ANN (with architecture 64-32-3), which seems to be best from all of our testings, that can predict the loading coefficients (a, b and c). And 2 more ANN's with (64-32-2, 64-32-3) for Linear Unloading and Exponential Unloading were trained. We used 'MSE', 'RMSE', 'MAE' as our metric and 'AIC', 'BIC' scores to compare the perfromance w.r.t complexity of different architectures.

At the end, after vigorous and careful hyper parameter tuning, we were able to achieve good scores, with the predicted values being close to the actual values.


![f928b0a7-5068-44c2-884c-820ce2735e57](https://github.com/pbt12/BTP-1-Prediction-of-Loading-and-Unloading-Charecteristics-/assets/74967927/04784127-447d-4651-af5b-4792a1e5a2d0)

Above image is the scatter plot of actual and predicted a_UL, b_UL, and c_UL (for exponential unloading scenario). We can see that the actual values are close to the predicted values. Apart from this, we trained another ANN to identify whether the unloading phase follows linear or exponential fashion, once we found out what type it follows, then we use the particular type ANN and get the plot or charecteristic.



The file 'Loading_Unloading_fit.ipynb' contains the code that I implemented for the above work.






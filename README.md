# Data-generation: 
In file original_dataset.csv, we put the original values of the training times with  limited number of AIFs and CPU cores
In file synthetic_dataset.csv, we put the synthetic values of the training time. We generate this dataset as follows:

Input: training time in function of the number of AIFs (2,4,6) and the number of CPU cores (1,2,4,6,8). 
1- We need to extend the number of CPU cores (until 16 cpu cores) using data fitting

2- Subsets of the dataset: we create one sub-dataset for each number of CPU (1,2,4,8). The format of the dataset is (#AIFs, training time) for each different CPU core number.

3- Once we have the complete data (training times for 2,4,6 AIFs with 1,2..16 CPU cores), we generate a larger dataset (data fitting) for each cpu core to have training times for 2,3,4,..,16 AIFs (Note that we do note consider the case of one AIF as this is generated for Federated learning applications)

4- Final data fitting for the whole dataset (#AIFs, #CPU, training time) to complete the missing values of #AIFs and #CPU.

** data fitting using the piecewise linear approximation function (pwlf in python)

# Credit-Card-Increase-Model-Card

### Basic Information

* **Person or organization developing model**: Harshit Aggarwal,'haggarwal17@gwmail.gwu.edu', Basil Punnus,'basilpunnus@gwmail.gwu.edu'
* **Model date**: August, 2021
* **Model version**: 1.0
* **License**: 
* **Model implementation code**: [DNSC_6301_10_GroupProject.ipynb](DNSC_6301_10_GroupProject.ipynb)

### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301_10 Project.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data
* **Source of training data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500
* ** Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | input | int | number of males and females
| **RACE** | input | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | input | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | input | int | 1 = married; 2 = single; 3 = others |
| **AGE** | input | float | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |


### Test Data
* **Source of test data**: GWU Blackboard, email `jphall@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None


### Model Details
* **Columns used as inputs in the final model**: X_names = ['LIMIT_BAL', 'PAY_0', 'PAY_2', 'PAY_3', 'PAY_4', 'PAY_5', 'PAY_6', 'BILL_AMT1', 'BILL_AMT2', 'BILL_AMT3', 'BILL_AMT4', 'BILL_AMT5', 'BILL_AMT6', 'PAY_AMT1', 'PAY_AMT2', 'PAY_AMT3', 'PAY_AMT4', 'PAY_AMT5', 'PAY_AMT6']
* **Column(s) used as target(s) in the final model**: y_name = 'DELINQ_NEXT' 
* **Type of model**:  Decision tree
* **Software used to implement the model**: ython, sc-kit-learn, google colab, pandas, matplotlib, numpy, io 
* **Version of the modeling software**: Python 3.7.11 Sklearn version 0.22.2.post1
* **Hyperparameters or other settings of your model **: Max_depth = 12    pre-bias remediation cutoff: 0.15   Post-bias remediation cutoff: 0.18

### Quantitative analysis
* **Metrics used to evaluate your final model**: Training AUC, Test AUC, Validation AUC, Asian-to-white AIR, Black-to-white AIR, hispanic-to-male AIR, Female-to-male AIR
* **State the final values of the metrics for all data: training, validation, and test data**: Training AUC: 0.774612  Validation AUC: 0.749614  Test AUC: 0.7454
* **Provide any plots related to your data or final model **:
![download (3)](https://user-images.githubusercontent.com/89624534/131265798-7a2afc0b-20ec-4d16-aac6-d34b2102a94f.png)
![Decision tree](https://user-images.githubusercontent.com/89624534/131274423-6631bb65-b1af-49b4-835f-84a15bd79c91.png)
![histogram](https://user-images.githubusercontent.com/89624534/131265485-7a169c38-50df-42be-98d3-0669b51085d5.png)
![download](https://user-images.githubusercontent.com/89624534/131265758-8ba45e28-d6ae-4dac-9215-f3c0a5f56ea1.png)
![download (1)](https://user-images.githubusercontent.com/89624534/131265761-5deb7900-a5b3-4e60-9cb8-54d6d4445a78.png)
![download (2)](https://user-images.githubusercontent.com/89624534/131265765-84009903-9263-483e-95ed-bbd97558bc12.png)



## Ethical considerations
* **Describe potential negative impacts of using your model**: 
   * ■ Math or software problems 
      Many different versions of software will lead to different outputs and hence different decisions based where/how the model is applied
   * ■ Real-world risks:  
      *Racial bias is built-in to the data
      *Data poisoning which can lead to wrong/unethical outcomes
 * **Describe potential uncertainties relating to the impacts of using your model**:
   * ■ Math or software problems 
      Data security is uncertain, breaches can directly impact lot of people
   * ■ Real-world risks: who, what, when or how? 
      Data regulation will directly impact the model 
  * **Describe any unexpected or results**:
    * Hispanic-to-white AIR is below 0.80
    * Female-to-male AIR is above 1.00
     
 
 
   
 
      
      




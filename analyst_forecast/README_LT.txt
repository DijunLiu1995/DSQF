Contacts:
Tim Copeland - tlc340@nyu.edu
Jason Mellone - jm5491@stern.nyu.edu
Di Luo - dl3351@nyu.edu

Data Sources:
●   The CRSP S&P 500 dataset, located in datasets/spx_crsp and maintained by Yuan Ni <yuan.ni@nyu.edu> and Kaili Li <kaili.li@nyu.edu>
●   The IBES Details dataset, which contains analyst recommendations since 1992 published by Thomson Reuters
●   The IBES Actuals dataset which contains the actual earnings announcements since 1970 (but the dataset was activated by Reuters in 1999).

Dataset:
    AFE/df_prc_dist.csv:
        - The multi-index is [ticker, ern_date, qnum] , 61 columns ranging from -30,...,-1,0,1,....,30 corresponding to the number of days after the earnings announcement. 0 corresponds to the day of the earnings announcement.
    AFE/df_actual_ern.csv:
        - index is [ticker, ern_date, quarternum, analyst_id], and single column, actual_ern_value
    AFE/df_forecast.csv:
        - index is [ticker, ern_date, quarternum, analyst_id], with a single column, analyst_ern_forecast  
    Model/surprise_earn_df.csv:
        - input the different metrics of the analyst distribution and its surprise metrics that we calculated for every earnings event, as output variable which use a categorical variable y which is 1 every time the 10-day post-earnings stock return is in the top 10% or bottom 10% for the given quarter. 
    Model/full_dist_df.csv:
        - Input includes: The relative proportions of number analysts in each of the 10 quantiles of the forecast distribution and the sum of these proportions should be 1; The total number of analysts in this distribution; The standard deviation of this distribution; The full range of the distribution; The actual earning announcement value; Output Y as surprise_earn_df; Y_up as the top 10% stock return of  given quarter; Y_down as the bottom 10% stock return of  given quarter
  

Data Gathering:

AFE/Data Cleaning.ipynb - Clean and merge data for CRSP S&P 500 dataset, the IBES details dataset and the IBES actual dataset.
AFE/conditioning_on_analyst_surprise.ipynb - Merge df_actual_ern.csv and df_forecast.csvcsv and obtain different metrics of the analyst distribution

Models:
    Two class model 
        - SGDClassifier is used for classification;
        - This classification model  trained basing on surprise_earn_df.csv and full_dist_df.csv;
        - Log Loss and SVM Loss are used to train the Models;
        - GridSearch the parameters;
        - Precision/Recall And ROC Analysis and find which training dataset works best;
        - Year > 2016 of the data are used for training, Year < 2016 of the raw data are used for testing;

Model Evaluation:
    Precision - what fraction of the positive outcomes do we predict to be positive
    Recall - what fraction of our positive predictions are true positive

Note:
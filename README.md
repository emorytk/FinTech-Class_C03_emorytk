# FinTech-Class_C03_emorytk

Question: After reviewing the profit information across each date from the different time periods, can you identify any patterns or trends?

Answer: Based on the profit information and despite the sometimes extreme volatility, this was a strong market for crypto in the first three months of 2018. January started the year strong with a jump in price and profits. February had slower growth in the first half of the month yet finishes strong, and March continued the strong market of January.

**Note: In my last look through sections 7 and 8, the cumulative data may have been dupliicated, creating graphs that look exactly the same for the Per Trade and the Cumulative Numbers.

BELOW IS cHALLENGE 03

Crypto Arbitrage

In this Challenge, you'll take on the role of an analyst at a high-tech investment firm. The vice president (VP) of your department is considering arbitrage opportunities in Bitcoin and other cryptocurrencies. As Bitcoin trades on markets across the globe, can you capitalize on simultaneous price dislocations in those markets by using the powers of Pandas?

For this assignment, you’ll sort through historical trade data for Bitcoin on two exchanges: Bitstamp and Coinbase. Your task is to apply the three phases of financial analysis to determine if any arbitrage opportunities exist for Bitcoin.

This aspect of the Challenge will consist of 3 phases.

    Collect the data.

    Prepare the data.

    Analyze the data.

Import the required libraries and dependencies.

# import the pandas library

import pandas as pd

​

# import numpy library as np

#import numpy as np

​

# import the path module from the pathlib library

from pathlib import Path

​

# import additional libraries and dependencies

#import sys

​

#import the graph output

%matplotlib inline

Collect the Data

To collect the data that you’ll need, complete the following steps:

Instructions.

    Using the Pandas read_csv function and the Path module, import the data from bitstamp.csv file, and create a DataFrame called bitstamp. Set the DatetimeIndex as the Timestamp column, and be sure to parse and format the dates.

    Use the head (and/or the tail) function to confirm that Pandas properly imported the data.

    Repeat Steps 1 and 2 for coinbase.csv file.

Step 1: Using the Pandas read_csv function and the Path module, import the data from bitstamp.csv file, and create a DataFrame called bitstamp. Set the DatetimeIndex as the Timestamp column, and be sure to parse and format the dates.

# Read in the CSV file called "bitstamp.csv" using the Path module. 

# The CSV file is located in the Resources folder.

# Set the index to the column "Date"

# Set the parse_dates and infer_datetime_format parameters

​

# CANNOT FIGURE OUT WHAT'S WRONG HERE

bitstamp_df = pd.read_csv(

    Path("./Resources/bitstamp.csv"), 

    index_col="Timestamp", 

    parse_dates=True, 

    infer_datetime_format=True

)

​

# going back to simpler code because it works and allows me to finish the rest of the challenge.

#csvpath = Path("../Starter_Code/Resources/bitstamp.csv")

#bitstamp_df = pd.read_csv(csvpath)

Step 2: Use the head (and/or the tail) function to confirm that Pandas properly imported the data.

# Use the head (and/or tail) function to confirm that the data was imported properly.

bitstamp_df.head()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13681.04 	13681.04 	13637.93 	$13646.48 	3.334553 	45482.128785 	13639.647479
2018-01-01 00:01:00 	13646.48 	13658.75 	13610.18 	$13658.75 	2.663188 	36361.390888 	13653.332816
2018-01-01 00:02:00 	13616.93 	13616.93 	13610.06 	$13610.22 	0.084653 	1152.144036 	13610.136247
2018-01-01 00:03:00 	13610.27 	13639.09 	13610.27 	$13639.09 	7.182986 	97856.416478 	13623.361128
2018-01-01 00:04:00 	13635.35 	13636.35 	13620.00 	$13620.0 	1.069665 	14582.660932 	13632.923329

# use the tail function to confirm that the data was imported properly.

bitstamp_df.tail()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-03-31 23:55:00 	6935.01 	6939.07 	6922.56 	$6922.56 	1.044354 	7240.034602 	6932.550078
2018-03-31 23:56:00 	6922.02 	6922.02 	6918.00 	$6920.32 	3.069539 	21245.076275 	6921.260233
2018-03-31 23:57:00 	6920.33 	6936.42 	6920.33 	$6934.72 	28.239049 	195789.408220 	6933.286106
2018-03-31 23:58:00 	6927.65 	6929.42 	6927.65 	$6927.65 	0.839507 	5817.007705 	6929.080007
2018-03-31 23:59:00 	6929.98 	6929.98 	6928.00 	$6928.01 	0.209363 	1450.735763 	6929.289993
Step 3: Repeat Steps 1 and 2 for coinbase.csv file.

# Read in the CSV file called "coinbase.csv" using the Path module. 

# The CSV file is located in the Resources folder.

# Set the index to the column "Timestamp"

# Set the parse_dates and infer_datetime_format parameters

​

# CANNOT FIGURE OUT WHAT'S WRONG HERE

coinbase_df = pd.read_csv(

    Path("./Resources/coinbase.csv"), 

    index_col="Timestamp", 

    parse_dates=True, 

    infer_datetime_format=True

)

​

# going back to simpler code because it works and allows me to finish the rest of the challenge.

#csvpath = Path("../Starter_Code/Resources/coinbase.csv")

#coinbase_df = pd.read_csv(csvpath)

# Use the head (and/or tail) function to confirm that the data was imported properly.

coinbase_df.head()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13620.00 	13620.00 	13608.49 	$13608.49 	20.812754 	283451.08537 	13619.105106
2018-01-01 00:01:00 	13607.14 	13607.14 	13601.66 	$13601.66 	13.474359 	183283.97801 	13602.426919
2018-01-01 00:02:00 	13601.44 	13601.44 	13580.00 	$13580.0 	11.536360 	156789.19686 	13590.872506
2018-01-01 00:03:00 	13587.31 	13587.31 	13542.70 	$13550.34 	16.328039 	221413.64182 	13560.332806
2018-01-01 00:04:00 	13550.34 	13585.95 	13550.34 	$13583.44 	9.955364 	135141.26944 	13574.719401

# Use the head (and/or tail) function to confirm that the data was imported properly.

coinbase_df.tail()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-03-31 23:55:00 	6945.20 	6948.06 	6930.00 	$6930.0 	5.802288 	40243.918480 	6935.869979
2018-03-31 23:56:00 	6930.00 	6930.01 	6930.00 	$6930.01 	0.625053 	4331.620701 	6930.005567
2018-03-31 23:57:00 	6930.01 	6933.91 	6930.01 	$6933.91 	0.776431 	5382.532162 	6932.405747
2018-03-31 23:58:00 	6933.91 	6938.00 	6933.90 	$6937.31 	0.133413 	925.356547 	6936.048538
2018-03-31 23:59:00 	6937.30 	6937.30 	6931.09 	$6934.0 	1.012720 	7022.275088 	6934.070316
Prepare the Data

To prepare and clean your data for analysis, complete the following steps:

    For the bitstamp DataFrame, replace or drop all NaN, or missing, values in the DataFrame.

    Use the str.replace function to remove the dollar signs ($) from the values in the Close column.

    Convert the data type of the Close column to a float.

    Review the data for duplicated values, and drop them if necessary.

    Repeat Steps 1–4 for the coinbase DataFrame.

Step 1: For the bitstamp DataFrame, replace or drop all NaN, or missing, values in the DataFrame.

# For the bitstamp DataFrame, replace or drop all NaNs or missing values in the DataFrame

​

bitstamp_df = bitstamp_df.dropna()

​

#bitstamp_csv = Path("../Resources/bitstamp.csv)

#bitstamp_df - pd.read_csv(bitstamp_csv)

​

#daily_returns = pd.DataFrame.fillna("Unknown")

#daily_returns

# check data to see how many replacements are missing.

bitstamp_df

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13681.04 	13681.04 	13637.93 	$13646.48 	3.334553 	45482.128785 	13639.647479
2018-01-01 00:01:00 	13646.48 	13658.75 	13610.18 	$13658.75 	2.663188 	36361.390888 	13653.332816
2018-01-01 00:02:00 	13616.93 	13616.93 	13610.06 	$13610.22 	0.084653 	1152.144036 	13610.136247
2018-01-01 00:03:00 	13610.27 	13639.09 	13610.27 	$13639.09 	7.182986 	97856.416478 	13623.361128
2018-01-01 00:04:00 	13635.35 	13636.35 	13620.00 	$13620.0 	1.069665 	14582.660932 	13632.923329
... 	... 	... 	... 	... 	... 	... 	...
2018-03-31 23:55:00 	6935.01 	6939.07 	6922.56 	$6922.56 	1.044354 	7240.034602 	6932.550078
2018-03-31 23:56:00 	6922.02 	6922.02 	6918.00 	$6920.32 	3.069539 	21245.076275 	6921.260233
2018-03-31 23:57:00 	6920.33 	6936.42 	6920.33 	$6934.72 	28.239049 	195789.408220 	6933.286106
2018-03-31 23:58:00 	6927.65 	6929.42 	6927.65 	$6927.65 	0.839507 	5817.007705 	6929.080007
2018-03-31 23:59:00 	6929.98 	6929.98 	6928.00 	$6928.01 	0.209363 	1450.735763 	6929.289993

129067 rows × 7 columns
Step 2: Use the str.replace function to remove the dollar signs ($) from the values in the Close column.

# Use the str.replace function to remove the dollar sign, $

bitstamp_df["Close"] = bitstamp_df["Close"].str.replace("$", "")

C:\Users\emotracy\AppData\Local\Temp\ipykernel_5880\649469543.py:2: FutureWarning: The default value of regex will change from True to False in a future version. In addition, single character regular expressions will *not* be treated as literal strings when regex=True.
  bitstamp_df["Close"] = bitstamp_df["Close"].str.replace("$", "")

# checking to see if the $ were removed

bitstamp_df.head()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13681.04 	13681.04 	13637.93 	13646.48 	3.334553 	45482.128785 	13639.647479
2018-01-01 00:01:00 	13646.48 	13658.75 	13610.18 	13658.75 	2.663188 	36361.390888 	13653.332816
2018-01-01 00:02:00 	13616.93 	13616.93 	13610.06 	13610.22 	0.084653 	1152.144036 	13610.136247
2018-01-01 00:03:00 	13610.27 	13639.09 	13610.27 	13639.09 	7.182986 	97856.416478 	13623.361128
2018-01-01 00:04:00 	13635.35 	13636.35 	13620.00 	13620.0 	1.069665 	14582.660932 	13632.923329

# checking to see if the $ were removed

bitstamp_df.tail()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-03-31 23:55:00 	6935.01 	6939.07 	6922.56 	6922.56 	1.044354 	7240.034602 	6932.550078
2018-03-31 23:56:00 	6922.02 	6922.02 	6918.00 	6920.32 	3.069539 	21245.076275 	6921.260233
2018-03-31 23:57:00 	6920.33 	6936.42 	6920.33 	6934.72 	28.239049 	195789.408220 	6933.286106
2018-03-31 23:58:00 	6927.65 	6929.42 	6927.65 	6927.65 	0.839507 	5817.007705 	6929.080007
2018-03-31 23:59:00 	6929.98 	6929.98 	6928.00 	6928.01 	0.209363 	1450.735763 	6929.289993
Step 3: Convert the data type of the Close column to a float.

# Convert the Close data type to a float

bitstamp_df["Close"] = bitstamp_df["Close"].astype(float)

# confirm the update happened by calling the dtypes function on the bitstamp_df

bitstamp_df["Close"].dtypes

dtype('float64')

Step 4: Review the data for duplicated values, and drop them if necessary.

# Review the data for duplicate values, and drop them if necessary

bitstamp_df.drop_duplicates()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13681.04 	13681.04 	13637.93 	13646.48 	3.334553 	45482.128785 	13639.647479
2018-01-01 00:01:00 	13646.48 	13658.75 	13610.18 	13658.75 	2.663188 	36361.390888 	13653.332816
2018-01-01 00:02:00 	13616.93 	13616.93 	13610.06 	13610.22 	0.084653 	1152.144036 	13610.136247
2018-01-01 00:03:00 	13610.27 	13639.09 	13610.27 	13639.09 	7.182986 	97856.416478 	13623.361128
2018-01-01 00:04:00 	13635.35 	13636.35 	13620.00 	13620.00 	1.069665 	14582.660932 	13632.923329
... 	... 	... 	... 	... 	... 	... 	...
2018-03-31 23:55:00 	6935.01 	6939.07 	6922.56 	6922.56 	1.044354 	7240.034602 	6932.550078
2018-03-31 23:56:00 	6922.02 	6922.02 	6918.00 	6920.32 	3.069539 	21245.076275 	6921.260233
2018-03-31 23:57:00 	6920.33 	6936.42 	6920.33 	6934.72 	28.239049 	195789.408220 	6933.286106
2018-03-31 23:58:00 	6927.65 	6929.42 	6927.65 	6927.65 	0.839507 	5817.007705 	6929.080007
2018-03-31 23:59:00 	6929.98 	6929.98 	6928.00 	6928.01 	0.209363 	1450.735763 	6929.289993

129067 rows × 7 columns

# remove all the duplicate data from bitstamp_df if there are any

bitstamp_df = bitstamp_df.drop_duplicates()

#bitstamp_df.drop_duplicates().sum()

​

# Call the head function to review the first 5 rows of the DataFrame

bitstamp_df.head()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13681.04 	13681.04 	13637.93 	13646.48 	3.334553 	45482.128785 	13639.647479
2018-01-01 00:01:00 	13646.48 	13658.75 	13610.18 	13658.75 	2.663188 	36361.390888 	13653.332816
2018-01-01 00:02:00 	13616.93 	13616.93 	13610.06 	13610.22 	0.084653 	1152.144036 	13610.136247
2018-01-01 00:03:00 	13610.27 	13639.09 	13610.27 	13639.09 	7.182986 	97856.416478 	13623.361128
2018-01-01 00:04:00 	13635.35 	13636.35 	13620.00 	13620.00 	1.069665 	14582.660932 	13632.923329
Step 5: Repeat Steps 1–4 for the coinbase DataFrame.

# Step 1: For the coinbase DataFrame, replace or drop all NaNs or missing values in the DataFrame

coinbase_df.dropna()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13620.00 	13620.00 	13608.49 	$13608.49 	20.812754 	283451.085370 	13619.105106
2018-01-01 00:01:00 	13607.14 	13607.14 	13601.66 	$13601.66 	13.474359 	183283.978010 	13602.426919
2018-01-01 00:02:00 	13601.44 	13601.44 	13580.00 	$13580.0 	11.536360 	156789.196860 	13590.872506
2018-01-01 00:03:00 	13587.31 	13587.31 	13542.70 	$13550.34 	16.328039 	221413.641820 	13560.332806
2018-01-01 00:04:00 	13550.34 	13585.95 	13550.34 	$13583.44 	9.955364 	135141.269440 	13574.719401
... 	... 	... 	... 	... 	... 	... 	...
2018-03-31 23:55:00 	6945.20 	6948.06 	6930.00 	$6930.0 	5.802288 	40243.918480 	6935.869979
2018-03-31 23:56:00 	6930.00 	6930.01 	6930.00 	$6930.01 	0.625053 	4331.620701 	6930.005567
2018-03-31 23:57:00 	6930.01 	6933.91 	6930.01 	$6933.91 	0.776431 	5382.532162 	6932.405747
2018-03-31 23:58:00 	6933.91 	6938.00 	6933.90 	$6937.31 	0.133413 	925.356547 	6936.048538
2018-03-31 23:59:00 	6937.30 	6937.30 	6931.09 	$6934.0 	1.012720 	7022.275088 	6934.070316

129322 rows × 7 columns

# Step 2: Use the str.replace function to remove the dollar sign, $

coinbase_df["Close"] = coinbase_df["Close"].str.replace("$", "")

#bitstamp_df["Close"] = bitstamp_df["Close"].str.replace("$", "")

C:\Users\emotracy\AppData\Local\Temp\ipykernel_5880\1604349770.py:2: FutureWarning: The default value of regex will change from True to False in a future version. In addition, single character regular expressions will *not* be treated as literal strings when regex=True.
  coinbase_df["Close"] = coinbase_df["Close"].str.replace("$", "")

# checking to see if the $ were removed

coinbase_df.head()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13620.00 	13620.00 	13608.49 	13608.49 	20.812754 	283451.08537 	13619.105106
2018-01-01 00:01:00 	13607.14 	13607.14 	13601.66 	13601.66 	13.474359 	183283.97801 	13602.426919
2018-01-01 00:02:00 	13601.44 	13601.44 	13580.00 	13580.0 	11.536360 	156789.19686 	13590.872506
2018-01-01 00:03:00 	13587.31 	13587.31 	13542.70 	13550.34 	16.328039 	221413.64182 	13560.332806
2018-01-01 00:04:00 	13550.34 	13585.95 	13550.34 	13583.44 	9.955364 	135141.26944 	13574.719401

#Step 3: # Convert the Close data type to a float

coinbase_df["Close"] = coinbase_df["Close"].astype(float)

# confirm the update happened by calling the dtypes function on the bitstamp_df

coinbase_df["Close"].dtypes

dtype('float64')

# Review the data for duplicate values, and drop them if necessary

coinbase_df.drop_duplicates()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13620.00 	13620.00 	13608.49 	13608.49 	20.812754 	283451.085370 	13619.105106
2018-01-01 00:01:00 	13607.14 	13607.14 	13601.66 	13601.66 	13.474359 	183283.978010 	13602.426919
2018-01-01 00:02:00 	13601.44 	13601.44 	13580.00 	13580.00 	11.536360 	156789.196860 	13590.872506
2018-01-01 00:03:00 	13587.31 	13587.31 	13542.70 	13550.34 	16.328039 	221413.641820 	13560.332806
2018-01-01 00:04:00 	13550.34 	13585.95 	13550.34 	13583.44 	9.955364 	135141.269440 	13574.719401
... 	... 	... 	... 	... 	... 	... 	...
2018-03-31 23:55:00 	6945.20 	6948.06 	6930.00 	6930.00 	5.802288 	40243.918480 	6935.869979
2018-03-31 23:56:00 	6930.00 	6930.01 	6930.00 	6930.01 	0.625053 	4331.620701 	6930.005567
2018-03-31 23:57:00 	6930.01 	6933.91 	6930.01 	6933.91 	0.776431 	5382.532162 	6932.405747
2018-03-31 23:58:00 	6933.91 	6938.00 	6933.90 	6937.31 	0.133413 	925.356547 	6936.048538
2018-03-31 23:59:00 	6937.30 	6937.30 	6931.09 	6934.00 	1.012720 	7022.275088 	6934.070316

129323 rows × 7 columns

# remove all the duplicate data from bitstamp_df if there are any

coinbase_df = coinbase_df.drop_duplicates()

​

# Call the head function to review the first 5 rows of the DataFrame

coinbase_df.head()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
Timestamp 							
2018-01-01 00:00:00 	13620.00 	13620.00 	13608.49 	13608.49 	20.812754 	283451.08537 	13619.105106
2018-01-01 00:01:00 	13607.14 	13607.14 	13601.66 	13601.66 	13.474359 	183283.97801 	13602.426919
2018-01-01 00:02:00 	13601.44 	13601.44 	13580.00 	13580.00 	11.536360 	156789.19686 	13590.872506
2018-01-01 00:03:00 	13587.31 	13587.31 	13542.70 	13550.34 	16.328039 	221413.64182 	13560.332806
2018-01-01 00:04:00 	13550.34 	13585.95 	13550.34 	13583.44 	9.955364 	135141.26944 	13574.719401
Analyze the Data

Your analysis consists of the following tasks:

    Choose the columns of data on which to focus your analysis.

    Get the summary statistics and plot the data.

    Focus your analysis on specific dates.

    Calculate the arbitrage profits.

Step 1: Choose columns of data on which to focus your analysis.

Select the data you want to analyze. Use loc or iloc to select the following columns of data for both the bitstamp and coinbase DataFrames:

    Timestamp (index)

    Close

# Use loc or iloc to select `Timestamp (the index)` and `Close` from bitstamp DataFrame

#bitstamp_sliced = bitstamp_df 

bitstamp_sliced = bitstamp_df.iloc[:, [3]]

#bitstamp_df.iloc['Time Stamp':'Close']

​

# Review the first five rows of the DataFrame

bitstamp_sliced.head()

	Close
Timestamp 	
2018-01-01 00:00:00 	13646.48
2018-01-01 00:01:00 	13658.75
2018-01-01 00:02:00 	13610.22
2018-01-01 00:03:00 	13639.09
2018-01-01 00:04:00 	13620.00

# Use loc or iloc to select `Timestamp (the index)` and `Close` from coinbase DataFrame

#coinbase_sliced = coinbase_df

coinbase_sliced = coinbase_df.iloc[:, [3]]

​

# Review the first five rows of the DataFrame

coinbase_sliced.head()

	Close
Timestamp 	
2018-01-01 00:00:00 	13608.49
2018-01-01 00:01:00 	13601.66
2018-01-01 00:02:00 	13580.00
2018-01-01 00:03:00 	13550.34
2018-01-01 00:04:00 	13583.44
Step 2: Get summary statistics and plot the data.

Sort through the time series data associated with the bitstamp and coinbase DataFrames to identify potential arbitrage opportunities. To do so, complete the following steps:

    Generate the summary statistics for each DataFrame by using the describe function.

    For each DataFrame, create a line plot for the full period of time in the dataset. Be sure to tailor the figure size, title, and color to each visualization.

    In one plot, overlay the visualizations that you created in Step 2 for bitstamp and coinbase. Be sure to adjust the legend and title for this new visualization.

    Using the loc and plot functions, plot the price action of the assets on each exchange for different dates and times. Your goal is to evaluate how the spread between the two exchanges changed across the time period that the datasets define. Did the degree of spread change as time progressed?

# Generate the summary statistics for the bitstamp DataFrame

#bitstamp_df['Open', 'High', 'Low', 'Close', 'BTC Volume', 'USD Volume', 'Weighted Price'].dtypes

#bitstamp_df.iloc[()].dtypes

#bitstamp_df.describe[0,4]

bitstamp_df.describe()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
count 	129067.000000 	129067.000000 	129067.000000 	129067.000000 	129067.000000 	1.290670e+05 	129067.000000
mean 	10459.993683 	10472.970114 	10446.214703 	10459.842453 	11.792878 	1.177496e+05 	10459.384448
std 	2315.909269 	2318.929342 	2312.331601 	2315.976088 	21.799938 	2.070551e+05 	2315.723480
min 	5945.950000 	5975.060000 	5920.720000 	5944.000000 	0.000039 	3.333436e-01 	5949.997212
25% 	8613.985000 	8621.655000 	8604.440000 	8613.370000 	1.711874 	1.773244e+04 	8613.587020
50% 	10145.300000 	10156.410000 	10131.740000 	10145.950000 	4.994095 	5.188050e+04 	10144.740411
75% 	11444.455000 	11453.990000 	11431.970000 	11444.810000 	12.717950 	1.313104e+05 	11443.791560
max 	17234.980000 	17234.990000 	17214.960000 	17234.980000 	580.646391 	5.483271e+06 	17227.810502

# Generate the summary statistics for the coinbase DataFrame

coinbase_df.describe()

	Open 	High 	Low 	Close 	BTC Volume 	USD Volume 	Weighted Price
count 	129322.000000 	129322.000000 	129322.000000 	129322.000000 	129322.000000 	1.293220e+05 	129322.000000
mean 	10449.213185 	10456.118514 	10441.872248 	10449.140958 	15.666556 	1.572565e+05 	10448.964130
std 	2317.194653 	2317.710389 	2316.570594 	2317.197419 	27.481647 	2.667879e+05 	2317.167139
min 	5882.300000 	5907.280000 	5873.000000 	5882.310000 	0.000442 	6.699174e+00 	5883.394912
25% 	8609.230000 	8613.872500 	8603.505000 	8609.230000 	2.999125 	3.071222e+04 	8609.135020
50% 	10137.440000 	10145.900000 	10127.880000 	10137.440000 	7.092572 	7.461366e+04 	10136.035004
75% 	11397.522500 	11400.000000 	11390.000000 	11397.237500 	16.954279 	1.754530e+05 	11396.970843
max 	17178.000000 	17178.000000 	17177.990000 	17177.990000 	959.084903 	1.152334e+07 	17177.995495

# Create a line plot for the bitstamp DataFrame for the full length of time in the dataset 

# Be sure that the figure size, title, and color are tailored to each visualization

bitstamp_df['Close'].loc['2018-01-01' : '2018-03-31'].plot(

    legend=True, figsize=(8,5), title="Q1 2018 - Bitstamp January 1, 2018 to March 31, 2018", color="blue")

<AxesSubplot:title={'center':'Q1 2018 - Bitstamp January 1, 2018 to March 31, 2018'}, xlabel='Timestamp'>

# Create a line plot for the coinbase DataFrame for the full length of time in the dataset 

# Be sure that the figure size, title, and color are tailored to each visualization

coinbase_df['Close'].loc['2018-01-01' : '2018-03-31'].plot(

    legend=True, figsize=(8,5), title="Q1 2018 - Coinbase January 1, 2018 to March 31, 2018", color="orange")

<AxesSubplot:title={'center':'Q1 2018 - Coinbase January 1, 2018 to March 31, 2018'}, xlabel='Timestamp'>

# Overlay the visualizations for the bitstamp and coinbase DataFrames in one plot

# The plot should visualize the prices over the full lenth of the dataset

# Be sure to include the parameters: legend, figure size, title, and color and label

bitstamp_df['Close'].loc['2018-01-01' : '2018-03-31'].plot(

    legend=True, figsize=(8,5), title="Q1 2018 - Bitstamp and Coinbase January 1, 2018 to March 31, 2018", color="blue")

coinbase_df['Close'].loc['2018-01-01' : '2018-03-31'].plot(

    legend=True, figsize=(8,5), color="orange")

<AxesSubplot:title={'center':'Q1 2018 - Bitstamp and Coinbase January 1, 2018 to March 31, 2018'}, xlabel='Timestamp'>

# Using the loc and plot functions, create an overlay plot that visualizes 

# the price action of both DataFrames for a one month period early in the dataset

# Be sure to include the parameters: legend, figure size, title, and color and label

bitstamp_df['Close'].loc['2018-01-18' : '2018-01-30'].plot(

    legend=True, figsize=(8, 5), title="Q1 2018 - Bitstamp and Coinbase Overlay Plot January 2018", color="blue", label="Bitstamp")

coinbase_df['Close'].loc['2018-01-18' : '2018-01-30'].plot(

    legend=True, figsize=(8, 5), color="orange", label="Coinbase")

<AxesSubplot:title={'center':'Q1 2018 - Bitstamp and Coinbase Overlay Plot January 2018'}, xlabel='Timestamp'>

# Using the loc and plot functions, create an overlay plot that visualizes 

# the price action of both DataFrames for a one month period later in the dataset

# Be sure to include the parameters: legend, figure size, title, and color and label 

bitstamp_df['Close'].loc['2018-03-01' : '2018-03-31'].plot(

    legend=True, figsize=(8, 5), title="Q1 2018 Bitstamp and Coinbase Overlay Plot March 2018", color="blue", label="Bitstamp")

coinbase_df['Close'].loc['2018-03-01' : '2018-03-31'].plot(

    legend=True, figsize=(8, 5), color="orange", label="Coinbase")

<AxesSubplot:title={'center':'Q1 2018 Bitstamp and Coinbase Overlay Plot March 2018'}, xlabel='Timestamp'>

Question Based on the visualizations of the different time periods, has the degree of spread change as time progressed?

Answer YOUR ANSWER HERE
Step 3: Focus Your Analysis on Specific Dates

Focus your analysis on specific dates by completing the following steps:

    Select three dates to evaluate for arbitrage profitability. Choose one date that’s early in the dataset, one from the middle of the dataset, and one from the later part of the time period.

    For each of the three dates, generate the summary statistics and then create a box plot. This big-picture view is meant to help you gain a better understanding of the data before you perform your arbitrage calculations. As you compare the data, what conclusions can you draw?

# Create an overlay plot that visualizes the two dataframes over a period of one day early in the dataset. 

# Be sure that the plots include the parameters `legend`, `figsize`, `title`, `color` and `label` 

bitstamp_df['Close'].loc['2018-01-18' : '2018-01-18'].plot(

    legend=True, figsize=(8, 5), title="Bitstamp and Coinbase Overlay Plot January 18, 2018", color="blue", label="Bitstamp")

coinbase_df['Close'].loc['2018-01-18' : '2018-01-18'].plot(

    legend=True, figsize=(8, 5), color="orange", label="Coinbase")

<AxesSubplot:title={'center':'Bitstamp and Coinbase Overlay Plot January 18, 2018'}, xlabel='Timestamp'>

# Using the early date that you have selected, calculate the arbitrage spread 

# by subtracting the bitstamp lower closing prices from the coinbase higher closing prices

arbitrage_spread_early = coinbase_df['Close'].loc['2018-01-18' : '2018-01-18'] - bitstamp_df['Close'].loc['2018-01-18' : '2018-01-18']

​

# Generate summary statistics for the early DataFrame

arbitrage_spread_early.describe()

count    1440.000000
mean      -10.069174
std        33.155183
min      -121.730000
25%       -31.970000
50%       -11.365000
75%        12.820000
max       113.300000
Name: Close, dtype: float64

# Visualize the arbitrage spread from early in the dataset in a box plot

arbitrage_spread_early.plot(kind='box')

<AxesSubplot:>

# Create an overlay plot that visualizes the two dataframes over a period of one day from the middle of the dataset. 

# Be sure that the plots include the parameters `legend`, `figsize`, `title`, `color` and `label` 

bitstamp_df['Close'].loc['2018-02-18' : '2018-02-18'].plot(

    legend=True, figsize=(8, 5), title="Q1 2018 - Bitstamp and Coinbase Overlay Plot February 18, 2018", color="blue", label="Bitstamp")

coinbase_df['Close'].loc['2018-02-18' : '2018-02-18'].plot(

    legend=True, figsize=(8, 5), color="orange", label="Coinbase")

​

<AxesSubplot:title={'center':'Q1 2018 - Bitstamp and Coinbase Overlay Plot February 18, 2018'}, xlabel='Timestamp'>

# Using the date in the middle that you have selected, calculate the arbitrage spread 

# by subtracting the bitstamp lower closing prices from the coinbase higher closing prices

arbitrage_spread_middle = coinbase_df['Close'].loc['2018-02-18' : '2018-02-18'] - bitstamp_df['Close'].loc['2018-02-18' : '2018-02-18']

​

​

# Generate summary statistics 

arbitrage_spread_early.describe()

count    1440.000000
mean      -10.069174
std        33.155183
min      -121.730000
25%       -31.970000
50%       -11.365000
75%        12.820000
max       113.300000
Name: Close, dtype: float64

# Visualize the arbitrage spread from the middle of the dataset in a box plot

arbitrage_spread_middle.plot(kind='box')

<AxesSubplot:>

# Create an overlay plot that visualizes the two dataframes over a period of one day from late in the dataset. 

# Be sure that the plots include the parameters `legend`, `figsize`, `title`, `color` and `label` 

bitstamp_df['Close'].loc['2018-03-18' : '2018-03-18'].plot(

    legend=True, figsize=(8, 5), title="Q1 2018 - Bitstamp and Coinbase Overlay Plot March 18, 2018", color="blue", label="Bitstamp")

coinbase_df['Close'].loc['2018-03-18' : '2018-03-18'].plot(

    legend=True, figsize=(8, 5), color="orange", label="Coinbase")

<AxesSubplot:title={'center':'Q1 2018 - Bitstamp and Coinbase Overlay Plot March 18, 2018'}, xlabel='Timestamp'>

# Using the date from the late that you have selected, calculate the arbitrage spread 

# by subtracting the bitstamp lower closing prices from the coinbase higher closing prices

arbitrage_spread_late = coinbase_df['Close'].loc['2018-03-18' : '2018-03-18'] - bitstamp_df['Close'].loc['2018-03-18' : '2018-03-18']

​

# Generate summary statistics for the late DataFrame

arbitrage_spread_late.describe()

count    1436.000000
mean       -8.675042
std        11.080605
min       -56.100000
25%       -15.852500
50%        -8.645000
75%        -1.245000
max        51.000000
Name: Close, dtype: float64

# Visualize the arbitrage spread from late in the dataset in a box plot

arbitrage_spread_late.plot(kind='box')

<AxesSubplot:>

Step 4: Calculate the Arbitrage Profits

Calculate the potential profits for each date that you selected in the previous section. Your goal is to determine whether arbitrage opportunities still exist in the Bitcoin market. Complete the following steps:

    For each of the three dates, measure the arbitrage spread between the two exchanges by subtracting the lower-priced exchange from the higher-priced one. Then use a conditional statement to generate the summary statistics for each arbitrage_spread DataFrame, where the spread is greater than zero.

    For each of the three dates, calculate the spread returns. To do so, divide the instances that have a positive arbitrage spread (that is, a spread greater than zero) by the price of Bitcoin from the exchange you’re buying on (that is, the lower-priced exchange). Review the resulting DataFrame.

    For each of the three dates, narrow down your trading opportunities even further. To do so, determine the number of times your trades with positive returns exceed the 1% minimum threshold that you need to cover your costs.

    Generate the summary statistics of your spread returns that are greater than 1%. How do the average returns compare among the three dates?

    For each of the three dates, calculate the potential profit, in dollars, per trade. To do so, multiply the spread returns that were greater than 1% by the cost of what was purchased. Make sure to drop any missing values from the resulting DataFrame.

    Generate the summary statistics, and plot the results for each of the three DataFrames.

    Calculate the potential arbitrage profits that you can make on each day. To do so, sum the elements in the profit_per_trade DataFrame.

    Using the cumsum function, plot the cumulative sum of each of the three DataFrames. Can you identify any patterns or trends in the profits across the three time periods?

(NOTE: The starter code displays only one date. You'll want to do this analysis for two additional dates).
1. For each of the three dates, measure the arbitrage spread between the two exchanges by subtracting the lower-priced exchange from the higher-priced one. Then use a conditional statement to generate the summary statistics for each arbitrage_spread DataFrame, where the spread is greater than zero.

NOTE: For illustration, only one of the three dates is shown in the starter code below.

# For the date early in the dataset, measure the arbitrage spread between the two exchanges

# by subtracting the lower-priced exchange from the higher-priced one

arbitrage_spread_early = coinbase_df['Close'].loc['2018-01-18'] - bitstamp_df['Close'].loc['2018-01-18']

​

# Use a conditional statement to generate the summary statistics for each arbitrage_spread DataFrame

arbitrage_spread_early.describe()

count    1440.000000
mean      -10.069174
std        33.155183
min      -121.730000
25%       -31.970000
50%       -11.365000
75%        12.820000
max       113.300000
Name: Close, dtype: float64

# For the date in the middle in the dataset, measure the arbitrage spread between the two exchanges

# by subtracting the lower-priced exchange from the higher-priced one

arbitrage_spread_middle = coinbase_df['Close'].loc['2018-02-18'] - bitstamp_df['Close'].loc['2018-02-18']

​

# Use a conditional statement to generate the summary statistics for each arbitrage_spread DataFrame

arbitrage_spread_middle.describe()

count    1436.000000
mean      -15.861741
std        18.735501
min       -73.230000
25%       -29.277500
50%       -15.820000
75%        -3.182500
max        55.590000
Name: Close, dtype: float64

2. For each of the three dates, calculate the spread returns. To do so, divide the instances that have a positive arbitrage spread (that is, a spread greater than zero) by the price of Bitcoin from the exchange you’re buying on (that is, the lower-priced exchange). Review the resulting DataFrame.

# For the date late in the dataset, measure the arbitrage spread between the two exchanges

# by subtracting the lower-priced exchange from the higher-priced one

arbitrage_spread_late = coinbase_df['Close'].loc['2018-03-18'] - bitstamp_df['Close'].loc['2018-03-18']

​

# Use a conditional statement to generate the summary statistics for each arbitrage_spread DataFrame

arbitrage_spread_late.describe()

count    1436.000000
mean       -8.675042
std        11.080605
min       -56.100000
25%       -15.852500
50%        -8.645000
75%        -1.245000
max        51.000000
Name: Close, dtype: float64

# For the date early in the dataset, calculate the spread returns by dividing the instances when the arbitrage spread is positive (> 0) 

# by the price of Bitcoin from the exchange you are buying on (the lower-priced exchange).

arbitrage_spread_early_return = arbitrage_spread_early[arbitrage_spread_early>0] / bitstamp_df['Close'].loc['2018-01-18']  

​

# Review the spread return DataFrame

arbitrage_spread_early_return.describe()

count    5.450000e+02
mean     2.092038e-03
std      1.587167e-03
min      8.333333e-07
25%      8.683986e-04
50%      1.757728e-03
75%      3.040329e-03
max      9.950205e-03
Name: Close, dtype: float64

# For the date in the middle of the dataset, calculate the spread returns by dividing the instances when the arbitrage spread is positive (> 0) 

# by the price of Bitcoin from the exchange you are buying on (the lower-priced exchange).

arbitrage_spread_middle_return = arbitrage_spread_middle[arbitrage_spread_middle>0] / bitstamp_df['Close'].loc['2018-02-18']  

​

# Review the spread return DataFrame

arbitrage_spread_middle_return.describe()

count    2.820000e+02
mean     1.031964e-03
std      8.939144e-04
min      9.310987e-07
25%      3.875364e-04
50%      8.071585e-04
75%      1.451122e-03
max      5.143826e-03
Name: Close, dtype: float64

# For the date at the end of the dataset, calculate the spread returns by dividing the instances when the arbitrage spread is positive (> 0) 

# by the price of Bitcoin from the exchange you are buying on (the lower-priced exchange).

arbitrage_spread_late_return = arbitrage_spread_late[arbitrage_spread_late>0] / bitstamp_df['Close'].loc['2018-03-18']  

​

# Review the spread return DataFrame

arbitrage_spread_late_return.describe()

count    308.000000
mean       0.000758
std        0.000809
min        0.000001
25%        0.000202
50%        0.000539
75%        0.001078
max        0.006892
Name: Close, dtype: float64

3. For each of the three dates, narrow down your trading opportunities even further. To do so, determine the number of times your trades with positive returns exceed the 1% minimum threshold that you need to cover your costs.

# For the date early in the dataset, determine the number of times your trades with positive returns 

# exceed the 1% minimum threshold (.01) that you need to cover your costs

profitable_trades_early = arbitrage_spread_early[arbitrage_spread_early > .01] #[arbitrage_spread_early > 0.01]

​

# Review the first five profitable trades

profitable_trades_early.head()

Timestamp
2018-01-18 00:01:00     8.89
2018-01-18 00:02:00    26.36
2018-01-18 00:03:00    11.93
2018-01-18 00:05:00    17.38
2018-01-18 00:08:00     3.95
Name: Close, dtype: float64

# For the date in the middle of the dataset, determine the number of times your trades with positive returns 

# exceed the 1% minimum threshold (.01) that you need to cover your costs

profitable_trades_middle = arbitrage_spread_middle[arbitrage_spread_middle > 0.01]

​

# Review the first five profitable trades

profitable_trades_middle.head()

Timestamp
2018-02-18 00:00:00    36.42
2018-02-18 00:01:00     6.13
2018-02-18 00:02:00    38.25
2018-02-18 00:03:00    22.11
2018-02-18 00:04:00    40.08
Name: Close, dtype: float64

# For the date at the end of the dataset, determine the number of times your trades with positive returns 

# exceed the 1% minimum threshold (.01) that you need to cover your costs

profitable_trades_late = arbitrage_spread_late[arbitrage_spread_late > 0.01]

​

# Review the first five profitable trades

profitable_trades_late.head()

Timestamp
2018-03-18 00:01:00    6.60
2018-03-18 00:02:00    0.71
2018-03-18 00:03:00    5.28
2018-03-18 00:07:00    4.26
2018-03-18 00:16:00    0.40
Name: Close, dtype: float64

4. Generate the summary statistics of your spread returns that are greater than 1%. How do the average returns compare among the three dates?

# For the date early in the dataset, generate the summary statistics for the profitable trades

# or you trades where the spread returns are greater than 1%

​

profitable_trades_early.describe()

count    545.000000
mean      23.895193
std       18.117911
min        0.010000
25%       10.000000
50%       20.100000
75%       34.840000
max      113.300000
Name: Close, dtype: float64

# For the date in the middle of the dataset, generate the summary statistics for the profitable trades

# or you trades where the spread returns are are greater than 1%

​

profitable_trades_middle.describe()

count    282.000000
mean      10.939078
std        9.518918
min        0.010000
25%        4.100000
50%        8.605000
75%       15.427500
max       55.590000
Name: Close, dtype: float64

5. For each of the three dates, calculate the potential profit, in dollars, per trade. To do so, multiply the spread returns that were greater than 1% by the cost of what was purchased. Make sure to drop any missing values from the resulting DataFrame.

# For the date early in the dataset, calculate the potential profit per trade in dollars 

# Multiply the profitable trades by the cost of the Bitcoin that was purchased

profit_early = profitable_trades_early * bitstamp_df['Close'].loc['2018-01-18']

profit_early

Timestamp
2018-01-18 00:00:00            NaN
2018-01-18 00:01:00     98777.7679
2018-01-18 00:02:00    293002.7348
2018-01-18 00:03:00    132519.2751
2018-01-18 00:04:00            NaN
                          ...     
2018-01-18 23:55:00            NaN
2018-01-18 23:56:00            NaN
2018-01-18 23:57:00            NaN
2018-01-18 23:58:00            NaN
2018-01-18 23:59:00            NaN
Name: Close, Length: 1440, dtype: float64

profit_per_trade_early = profit_early.dropna()

profit_per_trade_early.describe()

count    5.450000e+02
mean     2.730453e+05
std      2.070537e+05
min      1.125000e+02
25%      1.168135e+05
50%      2.339856e+05
75%      3.970904e+05
max      1.290113e+06
Name: Close, dtype: float64

profit_early_sum = profit_per_trade_early.sum()

profit_early.sum

<bound method NDFrame._add_numeric_operations.<locals>.sum of Timestamp
2018-01-18 00:00:00            NaN
2018-01-18 00:01:00     98777.7679
2018-01-18 00:02:00    293002.7348
2018-01-18 00:03:00    132519.2751
2018-01-18 00:04:00            NaN
                          ...     
2018-01-18 23:55:00            NaN
2018-01-18 23:56:00            NaN
2018-01-18 23:57:00            NaN
2018-01-18 23:58:00            NaN
2018-01-18 23:59:00            NaN
Name: Close, Length: 1440, dtype: float64>

# For the date in the middle of the dataset, calculate the potential profit per trade in dollars 

# Multiply the profitable trades by the cost of the Bitcoin that was purchased

profit_middle = profitable_trades_middle * bitstamp_df['Close'].loc['2018-02-18']

profit_middle

Timestamp
2018-02-18 00:00:00    398702.4870
2018-02-18 00:01:00     67226.7905
2018-02-18 00:02:00    417690.0000
2018-02-18 00:03:00    241261.8879
2018-02-18 00:04:00    437068.7928
                          ...     
2018-02-18 23:55:00            NaN
2018-02-18 23:56:00            NaN
2018-02-18 23:57:00            NaN
2018-02-18 23:58:00            NaN
2018-02-18 23:59:00            NaN
Name: Close, Length: 1436, dtype: float64

profit_per_trade_middle = profit_middle.dropna()

profit_per_trade_middle.describe()

count       282.000000
mean     115996.333135
std      101497.769286
min         104.790000
25%       43959.964800
50%       92047.714900
75%      164080.329125
max      600768.356700
Name: Close, dtype: float64

profit_per_trade_middle_sum = profit_per_trade_middle.sum()

profit_middle.sum

<bound method NDFrame._add_numeric_operations.<locals>.sum of Timestamp
2018-02-18 00:00:00    398702.4870
2018-02-18 00:01:00     67226.7905
2018-02-18 00:02:00    417690.0000
2018-02-18 00:03:00    241261.8879
2018-02-18 00:04:00    437068.7928
                          ...     
2018-02-18 23:55:00            NaN
2018-02-18 23:56:00            NaN
2018-02-18 23:57:00            NaN
2018-02-18 23:58:00            NaN
2018-02-18 23:59:00            NaN
Name: Close, Length: 1436, dtype: float64>

# For the date late in the dataset, calculate the potential profit per trade in dollars 

# Multiply the profitable trades by the cost of the Bitcoin that was purchased

profit_late = profitable_trades_late * bitstamp_df['Close'].loc['2018-03-18']

profit_late

Timestamp
2018-03-18 00:00:00           NaN
2018-03-18 00:01:00    50582.4000
2018-03-18 00:02:00     5441.4400
2018-03-18 00:03:00    40497.2832
2018-03-18 00:04:00           NaN
                          ...    
2018-03-18 23:55:00           NaN
2018-03-18 23:56:00           NaN
2018-03-18 23:57:00           NaN
2018-03-18 23:58:00           NaN
2018-03-18 23:59:00           NaN
Name: Close, Length: 1436, dtype: float64

profit_per_trade_late = profit_late.dropna()

profit_per_trade_late.describe()

count       308.000000
mean      46704.027537
std       49561.461187
min          74.000000
25%       12087.143475
50%       32828.602500
75%       64310.659200
max      377400.000000
Name: Close, dtype: float64

profit_late_sum = profit_per_trade_late.sum()

profit_late.sum

<bound method NDFrame._add_numeric_operations.<locals>.sum of Timestamp
2018-03-18 00:00:00           NaN
2018-03-18 00:01:00    50582.4000
2018-03-18 00:02:00     5441.4400
2018-03-18 00:03:00    40497.2832
2018-03-18 00:04:00           NaN
                          ...    
2018-03-18 23:55:00           NaN
2018-03-18 23:56:00           NaN
2018-03-18 23:57:00           NaN
2018-03-18 23:58:00           NaN
2018-03-18 23:59:00           NaN
Name: Close, Length: 1436, dtype: float64>

#### 6. Generate the summary statistics, and plot the results for each of the three DataFrames.

​

# Generate the summary statistics for the early profit per trade DataFrame

profit_early.describe()

count    5.450000e+02
mean     2.730453e+05
std      2.070537e+05
min      1.125000e+02
25%      1.168135e+05
50%      2.339856e+05
75%      3.970904e+05
max      1.290113e+06
Name: Close, dtype: float64

# plot the results for the early dataframe

profit_per_trade_early.plot(figsize=(10, 7), title="Profits")

<AxesSubplot:title={'center':'Profits'}, xlabel='Timestamp'>

# Generate the summary statistics for the middle profit per trade DataFrame

profit_middle.describe()

count       282.000000
mean     115996.333135
std      101497.769286
min         104.790000
25%       43959.964800
50%       92047.714900
75%      164080.329125
max      600768.356700
Name: Close, dtype: float64

# plot the results for the middle dataframe

profit_per_trade_middle.plot(figsize=(10, 7), title="Profits")

<AxesSubplot:title={'center':'Profits'}, xlabel='Timestamp'>

# Generate the summary statistics for the late profit per trade DataFrame

profit_late.describe()

count       308.000000
mean      46704.027537
std       49561.461187
min          74.000000
25%       12087.143475
50%       32828.602500
75%       64310.659200
max      377400.000000
Name: Close, dtype: float64

# plot the results for the late dataframe

profit_per_trade_late.plot(figsize=(10, 7), title="Profits")

<AxesSubplot:title={'center':'Profits'}, xlabel='Timestamp'>

7. Calculate the potential arbitrage profits that you can make on each day. To do so, sum the elements in the profit_per_trade DataFrame.

# Calculate the sum of the potential profits for the early profit per trade DataFrame

cumulative_profit_early = profit_per_trade_early.cumsum()

cumulative_profit_early.plot(figsize=(10, 7), title="Cumulative Profits Per Trade January 2018")

<AxesSubplot:title={'center':'Cumulative Profits Per Trade January 2018'}, xlabel='Timestamp'>

# Calculate the sum of the potential profits for the middle profit per trade DataFrame

cumulative_profit_middle = profit_per_trade_middle.cumsum()

cumulative_profit_middle.plot(figsize=(10, 7), title="Cumulative Profits Per Trade February 2018")

<AxesSubplot:title={'center':'Cumulative Profits Per Trade February 2018'}, xlabel='Timestamp'>

# Calculate the sum of the potential profits for the late profit per trade DataFrame

cumulative_profit_late = profit_per_trade_late.cumsum()

cumulative_profit_late.plot(figsize=(10, 7), title="Cumulative Profits Per Trade March 2018")

<AxesSubplot:title={'center':'Cumulative Profits Per Trade March 2018'}, xlabel='Timestamp'>

8. Using the cumsum function, plot the cumulative sum of each of the three DataFrames. Can you identify any patterns or trends in the profits across the three time periods?

# Use the cumsum function to calculate the cumulative profits over time for the early profit per trade DataFrame

cumulative_profit_early = profit_per_trade_early.cumsum()

cumulative_profit_early.plot(figsize=(10, 7), title="Cumulative Sum January 2018")

<AxesSubplot:title={'center':'Cumulative Sum January 2018'}, xlabel='Timestamp'>

# Plot the cumulative sum of profits for the early profit per trade DataFrame

cumulative_profit_late = profit_per_trade_late.cumsum()

cumulative_profit_late.plot(figsize=(10, 7), title="Cumulative Sum March 2018")

<AxesSubplot:title={'center':'Cumulative Sum March 2018'}, xlabel='Timestamp'>

Question: After reviewing the profit information across each date from the different time periods, can you identify any patterns or trends?



# Examining Income and Expenditure in Western Australia Over Time

### Project Description

Perform ETL process on three datasets to enable analysis of income and expenditure in Western Australia for a set time period.

## Extract

The following three datasets were used from the Australian Bureau of Statistics:

1. *Table 12e. Average weekly earnings, Western Australia (dollars) - seasonally adjusted*.
   - Format: XLSX
   - Link:- https://www.abs.gov.au/statistics/labour/earnings-and-working-conditions/averageweekly-earnings-australia/may-2022#data-download
2. *Table 8. Labour force status by Sex, Western Australia - Trend, Seasonally adjusted and Original*.
   - Format: XLSX
   - Link:- https://www.abs.gov.au/statistics/labour/employment-and-unemployment/labour-forceaustralia/oct-2022#states-and-territories
3. *Table 3. Retail Turnover, by state*.
   - Format: XLSX
   - Link:- https://www.abs.gov.au/statistics/industry/retail-and-wholesale-trade/retail-tradeaustralia/oct-2022#data-download
## Transform
The data was filtered to remove unnecessary rows (0-9) on all three dataframes so that the remaining values were Date in column 0 and columns >0 had the corresponding values for each relative date. Next we reduced the columns of each dataframe.

1. Average Weekly Earnings 
   - For the Average Weekly Earnings dataframe we removed column 1, 4, and 7 (Earnings for Male, Female, and Persons Full Time Ordinary Time Earnings WA) as we were only interested in the full time and part time earnings of Males, Females, and Persons in Western Australia.
   - The columns were renamed with more appropriate headings. 
<!--    - Column 0 was renamed from 'Unnamed: 0' to 'Date', 'Earnings; Males; Full Time; Adult; Total earnings ; Western Australia ;' was renamed 'Male Earnings Full Time ($)', 'Earnings; Males; Total earnings ; Western Australia ;' was renamed 'Male Earnings Total ($)', and the same format of renaming was followed for the two Females and Persons columns. -->
2. Labour Force
   - The columns for the Labour Force dataframe were filtered to only contain 7/85 columns using the iloc function in Jupyter Notebook. The columns kept were 0, 2, 5, 8, 11, 14, 17 and contained the Date, Employed Total Persons, Males and Females, and Employed Full Time Persons, Males and Females.
   - The seven columns kept were renamed to have more legible headings. Column 0 was renamed from 'Unnamed: 0' to 'Date' and the remaining 6 columns followed this transformation format: 'Employed total ; Persons ;.1' renamed 'Employed Total Persons (000)'.
3. Retail Turnover
   - Only two columns of 28 were kept in the filtering of the Retail Turnover dataframe, columns 0 and 14 by using the iloc function.
<!--    - Column 0 contained the date and was renamed appropriately. -->
<!--    - Column 14 contained the data on the total retail turnover in Western Australia for each respective date in the millions ($). This column was renamed from 'Turnover ; Western Australia ; Total (Industry) ;.1' to 'Retail Turnover WA ($ millions)' -->

To view the data as one singular table and ensure all the filtering was performed correctly, a new dataframe was created consisting of the *Average Weekly Income*, *Labour Force*, and *Retail Turnover* dataframes.
## Load
The dataframes are now ready to load into a local or cloud database.

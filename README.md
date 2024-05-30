# Interactive Map For Single and Double Storey Terraced Property Sale For 2022 In Melaka

## Project Overview 

This project proposes the creation of an interactive map that will contain detailed information about all the single storey and double storey terraced properties sold in Melaka in 2022. The map will serve as a tool for housing developers to develop effective pricing and business strategies for future developments in Melaka, taking into account the current market dynamics.   

In 2022, a total of 2870 transactions were made for single storey and double storey terraced houses in Melaka. The property sales for these houses amounted to RM869,477,476.00. These transactions include both freehold and leasehold properties, and cover 457 areas or schemes located in three districts Melaka Tengah, Alor Gajah, and Jasin.

The property market in the state is anticipated to maintain its upward trend, bolstered by the upcoming development projects. These include the Melaka Waterfront Economic Zone (MWEZ) with an expected completion date of 2035, and the ongoing construction of Harbour City Melaka by Hatten Land Ltd. These initiatives are set to have a positive impact on the state's property market.

![MWEZ.png](https://lh6.googleusercontent.com/u3S4EjKsun7Jt-ps9r-lcqcxqUaZU_ivDgh3LXEvsizJRh9AQ5GxMCVMOOpPoznHfpnCPnAHyP4jsPEH667fTL2Kq877bu0YduAXCWbptZ-6_uCgzvZhQ2We_Son0_FRQiFDOybG)

## Terraced Property Outlook

The property market in Melaka is interesting to watch with the launch of two exciting residential projects: Scientex Durian Tunggal 2 and Bandar Botani Parkland. These developments, spanning 202 acres of land, offer single and double storey terraced homes, making them a prime choice for homebuyers seeking quality living spaces. Keep an eye on these segments, as they are likely to be in high demand in the near future.

![SCIENTEX.png](https://scientex.com.my/wp-content/uploads/2021/09/Aerial-View-Photo.jpeg)

## Code and Resources Used

* __Jupyter Notebook Version__: 6.5.4
* __Packages__: pandas, numpy, scipy, matplotlib, seaborn, plotly express, sklearn
* __Dataset Source__: https://napic2.jpph.gov.my/ms/data-transaksi?category=36&id=241

## Dataset Information

[_**'dataset_2022.csv'**_](https://github.com/wafiesa/Codes/blob/master/dataset_2022.csv) contains data from National Property Information Centre (NAPIC).<br>
[_**'latlong.csv'**_](https://github.com/wafiesa/Codes/blob/master/latlong.csv) contains latitude and longitude information for scheme name/area. This lat and long information were built from https://postcode.my/location/melaka/ based on scheme name/area from dataset_2022.<br>
[_**'melaka_terraced_property_sales_2022.csv'**_](https://github.com/wafiesa/Codes/blob/master/melaka_terraced_property_sales_2022.csv) contains data generated from Jupyter Notebook following cleaning processes.

## [1. Data Cleaning](https://github.com/wafiesa/Codes/blob/master/Melaka_Terraced_Property_Sales_2022.ipynb)

In this part, we will begin our exploratory data analysis (EDA) by viewing the dataset_2022.csv.

#### Dataset overview

|	  |Property Type				      |District	  |Mukim				       |Scheme Name/Area			  |Month, Year of Transaction Date	 |Tenure		 |Land Area	 |Unit	 |Main Floor Area	|Transaction Price|
|---|---------------------------|-----------|------------------- |------------------------|----------------------------------|-----------|-----------|-------|-------------------|-----------------|
|0	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Alor Gajah	     |TAMAN SERI BAYU	        |October 2022	                     |Leasehold	 |143.0	     |sq.m	 |85.84	             |200000           |
|1	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	   |TAMAN BKT INDAH			    |July 2022							           |Freehold	 |143.0		   |sq.m	 |76.64				       |173000			     |
|2	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	   |TAMAN BKT INDAH			    |September 2022					           |Freehold	 |143.0	     |sq.m	 |77.01				       |210000           |
|3	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			     |TAMAN BELIMBING HARMONI	|October 2022						           |Leasehold	 |232.0	     |sq.m	 |75.72				       |361111           |
|4	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			     |TAMAN VISTA BELIMBING	  |January 2022						           |Freehold	 |128.0	     |sq.m	 |83.61				       |230000           |

🔶 Insights: The data contains 2870 rows with 10 columns.  

The dataset_2022.csv provides detailed information on property transactions, including property type, district, mukim, scheme name/area, transaction date (month and year), tenure, land area, unit, main floor area, and transaction price. This information is useful for exploratory analysis.

#### Data Cleaning

We have observed that the dataset expresses the 'Land Area' and 'Main Floor Area' in square meters (sq. meter). Although it is sufficient for performing exploratory data analysis, it is worth noting that square feet measurement is the most commonly used nomenclature in the real estate market to represent the size of a property.

We have convert the Land Area and Main Floor Area into square feet (sq.ft). Furthermore, we can conveniently rename the Land Area to Land Size and the Main Floor Area to Build Size. 

Moreover, we have successfully transformed the column 'Month, Year of Transaction Date' into a date column.
 
|	  |Property Type			        |District	  |Mukim				       |Scheme Name/Area			   |Month, Year of Transaction Date	|Tenure		  |Land Size	|Unit	  |Build Size	|Transaction Price|
|---|---------------------------|-----------|--------------------|-------------------------|--------------------------------|-----------|-----------|-------|-----------|-----------------|
|0	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Alor Gajah	     |TAMAN SERI BAYU	         |2022-10-01	                    |Leasehold	|1539.2377  |sq.ft	|923.9731	  |200000           |
|1	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	   |TAMAN BKT INDAH			     |2022-07-01							        |Freehold	  |1539.2377	|sq.ft	|824.9453		|173000			      |
|2	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	   |TAMAN BKT INDAH			     |2022-09-01					            |Freehold	  |1539.2377  |sq.ft	|828.9279		|210000           |
|3	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			     |TAMAN BELIMBING HARMONI  |2022-10-01						          |Leasehold	|2497.2248  |sq.ft	|815.0425		|361111           |
|4	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			     |TAMAN VISTA BELIMBING	   |2022-01-01						          |Freehold	  |1377.7792	|sq.ft	|899.9697		|230000           |

🔶 Insights: We have renamed a few columns and converted values for Land Size and Build Size to square feet measurement. 

#### Latitude and Longitude Positions

Before creating an interactive map, it is necessary to acquire the approximate latitude and longitude positions for each scheme name/area. As these positions are not included in the dataset, we can obtain them through the integration API between portal postcode.my and Google Maps.

|	  |Scheme Name/Area			  |Lat	    |Long		    |
|---|-----------------------|---------|-----------|
|0	|TAMAN SERI BAYU	      |2.384740 |102.212509 |
|1	|TAMAN BKT INDAH			  |2.350550	|102.103860 |
|2	|TAMAN BKT INDAH			  |2.350550 |102.103860 |
|3	|TAMAN BELIMBING HARMONI|2.335506	|102.266894 |
|4	|TAMAN VISTA BELIMBING  |2.328142	|102.266958 |

The portal provides access to 457 scheme names/areas, which can be leveraged to generate positions. However, the original dataset requires the integration of latitude and longitude positions to facilitate this process.

|	  |Property Type			        |District	  |Mukim				       |Scheme Name/Area			   |Lat       |Long       |Month, Year of Transaction Date |Tenure		  |Land Size	|Unit	  |Build Size	|Transaction Price|
|---|---------------------------|-----------|--------------------|-------------------------|----------|-----------|--------------------------------|------------|-----------|-------|-----------|-----------------|
|0	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Alor Gajah	     |TAMAN SERI BAYU	         |2.384740  |102.212509 |2022-10-01	                     |Leasehold	  |1539.2377  |sq.ft	|923.9731	  |200000           |
|1	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	   |TAMAN BKT INDAH			     |2.350550	|102.103860 |2022-07-01							         |Freehold	  |1539.2377	|sq.ft	|824.9453		|173000			      |
|2	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	   |TAMAN BKT INDAH			     |2.350550 |102.103860  |2022-09-01					             |Freehold	  |1539.2377  |sq.ft	|828.9279		|210000           |
|3	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			     |TAMAN BELIMBING HARMONI  |2.335506	|102.266894 |2022-10-01						           |Leasehold	  |2497.2248  |sq.ft	|815.0425		|361111           |
|4	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			     |TAMAN VISTA BELIMBING	   |2.328142	|102.266958 |2022-01-01						           |Freehold	  |1377.7792	|sq.ft	|899.9697		|230000           |

🔶 Insights: We have combined the latitude and longitute into the dataset_2022.csv and renamed it to melaka_terraced_property_sales_2022.csv.

Let's explore Melaka Property Sales Year 2022 with useful statistics, now that the dataset has been processed to the desired format.

## 2. Data Visualizations 

#### Statistics

![formatted_statistics.png](https://github.com/wafiesa/Codes/blob/master/formatted_statistics.png)

From the statistics summary above, we can observe that there were 2870 transactions made in the year 2022. 

The maximum transaction price was recorded at RM1.2 million while the minimum transaction price was clocked at RM90,000.00. The mean transaction price is RM302,953.82.

Since the dataset represents single storey and double storey terraced houses, we can visualize the data accroding to each type of property.

#### Boxplots

![Boxplot_for_Transaction_Price.png](https://github.com/wafiesa/Codes/blob/master/Boxplots_For_Transaction_Price.png)

The boxplots above illustrate the property types according to the districts. Furthermore, the boxplots also indicate the single storey terraced and double storey terraced houses by land status (tenure) for Freehold and Leasehold.

We can noticed that there are outliers it the boxplots but we want to retain it for visualization in the map.  

#### Heatmap

![Heatmap_District_Type.png](https://github.com/wafiesa/Codes/blob/master/Heatmap_District_Type.png)

The heatmap above shows the comparisson between property types and the districts. Melaka Tengah sees more single storey terraced sold in 2022 at 969 units comparing to Jasin of 471 units while Alor Gajah of 375 units.

While sale transactions of double storey terraced sold in Melaka is recorded highest in Melaka Tengah at 646 units followed by Alor Gajah of 313 and Jasin of 96 units.

![type_counts.png](https://github.com/wafiesa/Codes/blob/master/type_counts.png)

Overall, single storey terraced houses were sold a total of 1815 units compared to 1055 units of double storey terraced houses.

![Heatmap_District_Tenure](https://github.com/wafiesa/Codes/blob/master/Heatmap_District_Tenure.png)

![district_count](https://github.com/wafiesa/Codes/blob/master/district_counts.png)

From the heatmap of district versus tenure above we can observe that majority transactions were concenrated in Melaka Tengah district with 1615 units sold followed by Alor Gajah at 688 units and Jasin at 567 units.

In the aspect of tenure, freehold property are more preferred with 1633 representing 854 units from Melaka Tengah, 468 units and 311 unit for Jasin. 

Meanwhile leasehold residentials were recorded at 1237 transactions representing 761 units in Melaka Tengah, 256 units in Jasin and 220 units in Alor Gajah.

#### Interactive Map

![map_all.png](https://github.com/wafiesa/Codes/blob/master/map_all.png).<br>**Map 1: Hotspots for overall locations.** 

Using latitude and longitude information, we can scatter plot using plotly.express package to visualize the approximate positions for every scheme name/area. Off course, the interactive features do not available here but by running the codes it is so much interesting. Your can obtain some of information when you hover the map.

From the figure above, we can see that yellow circle represents higher transaction price and easy to locate on the map. The position of yellow circle represent most higher value transaction is located in Taman Residence Lapan, Melaka Tengah.

Similarly, the most concentrated dots are located in Melaka Tengah as it is near to central business district (CBD). This followed by the Bandar Botani Parkland where it records 124 transactions in 2022.

![map_all_count.png](https://github.com/wafiesa/Codes/blob/master/map_all_count.png).<br>**Map 2: Hotspots for transactions.** 

Figure above shows the transactions count over the scheme name/area. It is contradictory with previous plot map since the most transactions count were outside Melaka Tengah.

Specifically, the highest count was recorded at 154 transactions located in Taman Scientex (Bukit Tambun Perdana) in the proximity Durian Tunggal, Alor gajah.

![map_1stry.png](https://github.com/wafiesa/Codes/blob/master/map_1stry.png).<br>**Map 3: Hotspots for single storey locations.**

Figure above displays the locations for every single storey terraced sold in 2022. Ideally, Melaka Tengah seems to be very active in terms of populated dots on the map.  

![map_1stry_count.png](https://github.com/wafiesa/Codes/blob/master/map_1stry_count.png)<br>**Map 4: Hotspots for single storey transactions.** 

However, records show that Jasin was attractive enough to pull homebuyers in 2022. The transactions count were recorded at 124 in Botani Parkland alone. Additionally, high value residential such Country Villa in Jasin was also contributing atleast 44 transactions.

![map_2stry.png](https://github.com/wafiesa/Codes/blob/master/map_2stry.png),<br>**Map 5: Hotspots for double storey locations.**

In 2022, 1085 units of double storey terraced were sold in Melaka. Although Taman Anggerik (Lot 71) in Melaka Tengah recorded the highest market value for double storey of RM390,000.00 but it has serious contender from Jasin which is Country Villas at RM380,000.00. Both the residentials have almost identical build size of 1537.95 and 1471.75 respectively.     

![map_2stry_count.png](https://github.com/wafiesa/Codes/blob/master/map_2stry_count.png).<br>**Map 6: Hotspots for double storey transactions.**

Nevertheless, Alor Gajah seems has stole a spotlight since the highest transactions count was recorded in Taman Scientex (Bukit Tambun Perdana). The new development in Alor Gajah has managed to attract homebuyers to settle in the district. 

## 3. The Insights

#### Regression Analysis

![distplot_price.png](https://github.com/wafiesa/Codes/blob/master/distplot_price.png) ![distplot_build.png](https://github.com/wafiesa/Codes/blob/master/distplot_build.png)

From the density plot above, we can observe that the price range for the transactions is concentrated between RM200,000.00 up to RM300,000.00. Now, this explains that the density for build size is in the region between 800 sq.ft to 900 sq.ft.

The densities demonstrate that high purchase volume for the residential in the price range as well as the build size in concern. 

Using linear regression model, we can determined the coefficient among dependend and independend variables. From the computation in sklearn.linear_model package, the results for the variables are as follows:

Coefficient: [195.0251, 55.3691]
Intercept: -12227.5884

Thus, the regression can be represent as in the model below: 

![MLR.png](https://github.com/wafiesa/Codes/blob/master/MLR.png)

## Recommendations

#### Utilize Interactive Map for Market Analysis

Housing developers should leverage the interactive map to conduct in-depth market analysis by exploring transaction patterns, pricing trends and demand hotspots across different scheme name/areas in Melaka. This will facilitate informed decision-making in formulating pricing strategies and identifying lucrative development opportunities.

#### Monitor Future Development Projects 

Given the anticipated growth momentum in Melaka's property market, it's crucial for developers to closely monitor upcoming development projects such as Melaka Waterfront Economic Zone (MWEZ) and Harbour City Melaka. These projects are expected to drive demand and reshape the landscape of the property market, presenting potential investment opportunities.

#### Adapt Business Strategies

Based on the insights derived from the interactive map and market analysis, housing developers should adapt their business strategies accordingly. This may involve diversifying product offerings, targeting specific customer segments, or adjusting pricing strategies to remain competitive in the dynamic market landscape.

#### Enhance Customer Engagement

The interactive map can also serve as a valuable tool for enhancing customer engagement and marketing efforts. Developers can leverage the map to provide potential buyers with detailed information about available properties, amenities and surrounding infrastructure, thereby improving transparency and fostering trust with customers.

#### Collaborate with Stakeholders

Collaboration with local authorities, real estate agencies and other stakeholders can further enhance the effectiveness of the interactive map and promote sustainable growth in the property market. By sharing data and insights, stakeholders can collectively address challenges, identify opportunities and contribute to the overall development of Melaka's property sector.

## Conclusion

In conclusion, the development of an interactive map for single and double storey terraced property sales in Melaka for the year 2022 offers valuable insights and opportunities for housing developers. A comprehensive dataset covering transaction details, property attributes and geographic information, developers can gain a deeper understanding of market dynamics and consumer preferences.

The analysis revealed that Melaka's property market recorded significant transactions in 2022, with single and double storey terraced properties accounting for a substantial portion of the market activity. Key insights such as pricing trends, demand hotspots and upcoming development projects provide developers with actionable information to formulate effective business strategies and capitalize on emerging opportunities.

Moving forward, it is recommended that developers leverage the interactive map to conduct detailed market analysis, monitor future development projects, adapt business strategies, enhance customer engagement and collaborate with stakeholders. By doing so, developers can navigate the evolving property landscape in Melaka and drive sustainable growth in the industry.

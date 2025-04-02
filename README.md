# Mobile Sales Dashboard Report

### Dashboard Link : https://app.powerbi.com/groups/me/reports/384d017e-e935-44dc-9e7d-1626c1a36de1/ReportSection

## Problem Statement

This Mobile Sales Dashboard is designed for business decision-makers in the mobile phone industry—likely for a retailer, distributor, or brand analyzing sales performance. It helps to track sales by city, brand, and model.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a excel file.
- Step 2 : Open power query editor & using the ETL tools Data cleaning and processing was done.
- Step 4 : It was observed that some columns needed modifications and hence it was done.
     
  (i) Day, Month, and Year columns.
  
    these terms were allocated different column each but the analysis demanded them to be combined and hence it was done using merge column option.

     ![Image](https://github.com/user-attachments/assets/d8aaa5f3-2eab-4c89-9b9d-c0ac5b241552)
  
     ![Image](https://github.com/user-attachments/assets/1fa4d3d0-20e2-4b60-a3cd-9bd7eab6a0a0)

  (ii) Day Name column.

    this column had some mix kind of data, which could be done using Replace Values or even Date Option but it will just show the day name for only those dates which are present in the data. but we want each and every day from those 4 years to do the analysis. So to deal with it Custome calender table was made.
  
    ![Image](https://github.com/user-attachments/assets/68013721-8309-4256-96f9-d859ead37b3e)
	 
   (iii) Custome Calender Table.
  
  It was made so that we can get the Day Name for each and every date present in that particular year.
		 following formula was used to get that info and later it was converted into the column:
  
         =List.Dates(#date(2021,1,1),1461,#duration(1,0,0,0))
  
     ![Image](https://github.com/user-attachments/assets/3d56d1ad-4f14-46ef-ba73-20e4a41981c8)
 

 - Step 5 : Data Modeling

   i.e relationship was created between two tables.
          ![Image](https://github.com/user-attachments/assets/3937402a-7ac9-4eb1-b658-2d73a3c8c459) 
		  
		  
- Step 5 : Doing required DAX calculations
  
     New Measure where added:
            
   (a) Total_quantity
		
		        Total_quantity = SUM(Sales_Data[units sold])
			 
  (b) Total_sales 
		   
		        Total_sales = SUMX(Sales_Data,Sales_Data[Units sold]*Sales_Data[Price Per Unit])
         
  (c) Total_transactions
		
		       Transactions = COUNTROWS(sales_Data)
			 
  (d) Average_Price 

            Average_Price = AVERAGE(Sales_Data[Price Per Unit])

 - Step 5 : Dash Board Creation
      Dashboard was created using different charts, tables, cards, slicers, map, text box to get the insites regarding various terms.
  
  - Step 5 : Month To Day (MTD) Calculation and dashboard Creation
      MTD for total sales was calculated using formula:
	    
		 MTD = TOTALMTD([Total_Sales],Custome_Calender[Date].[Date])
  
  
  - Step 5 : Same Period Last Year Calculation and dashboard Creation
      
	  To compare last years sales with this year using formula:
	  
	     Same Period Last Year = CALCULATE([Total_Sales], SAMEPERIODLASTYEAR(Custome_Calander[Date].[Date]))
		  
		  

# Snapshot of Dashboard (Power BI DESKTOP)

![Image](https://github.com/user-attachments/assets/01bbdfbb-f119-483d-a66c-ff4717381b34)

 
 # Final Dashboard Snapshots

   ![Image](https://github.com/user-attachments/assets/41fc63a8-3afc-4bd0-bfc8-ba3f33deaa80)
   
   - MTD Dashboard Snapshot
   
    ![Image](https://github.com/user-attachments/assets/9cf47024-0ac1-44dd-bd6f-05b98af5051c)
	
   - Same Period Last Year Dashboard Snapshot
   
     ![Image](https://github.com/user-attachments/assets/f417bcce-5ac0-49e3-aa6c-0400c317f370)













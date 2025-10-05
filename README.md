STEP 1: Clean and Prepare the Dataset
Tool: Power BI Power Query
Task 1: Clean “Bag Weight”
1.	Open the CSV in Excel
2.	Column: Bag Weight (e.g., “35 kg”)
o	Use Find & Replace: Replace kg with nothing
o	Format the column as Number

Task 2: Clean “Altitude”
•	Values like "1700-1930" or "1200"
•	You want two columns: Altitude_Min, Altitude_Max
 Power BI:
1.	Go to Transform Data
2.	Right-click column → Split by Delimiter → Choose “-”
3.	Rename to Altitude_Min, Altitude_Max

Task 3: Convert Dates
•	Columns: Grading Date, Expiration
1.	In Excel: Change column format to Date
2.	In Power BI:
o	Select column
o	In ribbon, choose Data Type → Date

Task 4: Handle Missing Values
Columns like Variety, Processing Method, Region might be missing.
In Power BI:
•	Open Power Query (Transform Data)
•	Right-click column → choose Replace Errors or Fill Down
•	Or filter out null rows using the filter arrow

Task 5: Add Total Defects Column
In Power BI:
1.	Go to Modeling tab
2.	Click New Column
DAX Code :
Total_Defects = 'Table'[Category One Defects] + 'Table'[Category Two Defects]


Import the Data into Power BI
1.	Open Power BI Desktop
2.	Click Home → Get Data → Text/CSV
3.	Select your cleaned CSV file
4.	Click Load
5.	Click Transform Data to inspect and clean further if needed

1.What are the key determinants of coffee quality as evaluated through sensory attributes such as aroma, flavor, acidity, etc.?
Create Visuals for Research Questions
RQ1: Key Sensory Determinants
Visual 1: Bar Chart of Sensory Scores
1.	Visual: Clustered Bar Chart
2.	Axis: Aroma, Flavor, Acidity, etc.
3.	Values: Average of each field
Visual 2: Key Influencers
1.	Add Key Influencer Visual
2.	Analyze field: Total Cup Points
3.	Add sensory fields as inputs
 

2.Is there a correlation between processing methods, origin regions, and coffee quality scores?
RQ2: Processing Methods and Regions
Visual 1: Filled Map
1.	Add Map visual
2.	Location: Country of Origin
3.	Value: Average of Total Cup Points
Visual 2: Matrix
•	Rows: Processing Method
•	Columns: Country
•	Values: Total Cup Points (Average)
 Slicers:
•	Add Slicer Visuals for:
o	Processing Method
o	Harvest Year
 

3.Can we identify any trends or patterns in defect occurrences and their impact on overall coffee quality?
RQ3: Defects and Cup Score
Visual 1: Scatter Plot
•	X: Total_Defects
•	Y: Total Cup Points
Visual 2: Bar Chart
•	Axis: Category One Defects
•	Value: Average Total Cup Points
 

4.How do different variables interact to influence the Total Cup Points, which represent an overall measure of coffee quality?
RQ4: Interactions with Total Cup Points
 Visual 1: Decomposition Tree
•	Analyze: Total Cup Points
•	Explain by: Aroma, Region, Sweetness, etc.
 Visual 2: What-If Parameters
1.	Go to Modeling → New Parameter
2.	Name: "Aroma Score Slider", range 6 to 10
3.	Create Measure:
DAX Code :
Simulated_Score =[Aroma Score Slider Value] +[Acidity Score Slider Value] +[Flavor Score Slider Value]
 

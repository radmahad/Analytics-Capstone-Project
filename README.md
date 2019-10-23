**Apple Inc. Study**

Introduction

For this project, I was supplied with Customer Service Data for Apple Inc., a technology innovation giant popular for designing high quality computing tools (Macintosh), operating software (IOS), mobile media and computing devices (IPad, IPhone). As of 2018, Apple Inc. was the first US company to reach a valuation of 1 trillion USD, a far distance from its IPO in 1980, with its share value increasing significantly.  The customer service data is specifically related to their powerful mobile computing product, the Ipad, which Apple Inc. describes as &quot;Like a computer but unlike any computer.&quot; Since Apple was the first to bring such a product to market, it has experienced a steep learning curve in terms of improvements in their operating system, graphics and user interface and this has allowed them to stay ahead of other companies that entered this segment of the computing innovation industry such as Amazon (Fire), Lenovo, Samsung and Microsoft.

Delving deeper, the purpose of this project is to estimate the effect of help desk employment level on number of complaints received by Apple&#39;s customer service. Apple places great importance upon customer experiences, including customer complaints with staff being thoroughly trained in problem solving. (Genius Bar) However, it also has a large amount of customers posting negative customer service reviews online, indicating that its help services may not be at the level that is expected of the company. The estimation was conducted by cleaning the dataset using VBA to return panel data in a manner that enables statistical exploration and analysis, using defined variables that affect the number of complaints received.

Technical Execution and Technical Discussion

To be able to manipulate the data in a meaningful way, it was imported to Stata so that regression analyses could be run to understand the relationship between the numbers of complaints received and help desk employment level. Both, a dummy variable regression and within estimator (fixed effects) were used to estimate the relationship, as they fit best with the panel data.

First, to gain a basic understanding of the relationship, I created a scatterplot on Stata (Appendix) of the log of complaints received on the number of helpdesk employees which indicated that with a larger a number of employees present there is a lower number of complaints. To further discern the relationship, a basic regression was conducted by regressing the log of HelpDeskEmployees on the log of Complaints, but it is important to consider that this regression contains endogeneity and the log of complaints will be affected by more than just one variable and therefore is not an accurate measure of the relationship.

Equation: LogofComplaints = β0 + β1 (LogofHelpDeskEmployees) + e

Command: reg LogofComplaints LogofHelpDeskEmployees


The β1 of -2.4588 indicates that with a 1% increase in the number of help desk employees, there is a  2.4588% decrease in the number of complaints received. This follows rationality, and confirms that the relationship indicated by the graph is true. However, the number of complaints will be affected by a significant number of other terms currently in the error term that must be controlled for.

When considering variables to include in the project, the following variables were chosen, after the data was identified as panel data.

Log of Help Desk Employees: Involvement level of help desk employees is the key Independent (explanatory) variable in the understanding of its effect on the number of complaints received, ceteris paribus.

Log of Complaints: This is the dependent variable being studied, the number of complaints received in relation to the Apple Ipad.

Month: The data is a time series, with the population data being sampled over 4 years. Including a time variable could allow for insights such as whether there was a large number of complaints in a month due to a specific OS update or Ipad model, and this insight can be used to understand Apple&#39;s learning curve or where they need to make improvements. When exploring this variable, a graph (Appendix) was created to check for seasonality, but returned significant variation but no seasonality, eliminating an exploratory regression consideration of the effect of month on number of complaints and a within estimator was chosen instead of a simple regression.

Region: The data is panel data with the population data including 8 different regions. There may be more complaints in one region over the other and it is interesting to explore this variable, because in terms of operations of the company, if a region has more complaints about a specific IPad model, that region may have sold faulty models or other reasons for variation may be present.

Avg. Worker Hours (per day): Assuming that this variables reflects the number of hours worked by a help desk employee, it may have an effect on number of complaints. If a worker has worked more hours in a day, they may not be able to resolve the complaint as quickly due to tiredness or they may work through problems quicker if they deal with a number of similar problems in a day.

Local Unemployment: Unemployed individuals may not have the income to buy and use a computer, and thus use an Ipad, and if they are Unemployed, they may spend a larger amount of time on the device. This may lead to a need for maintenance from too much usage or the clarification of certain features as they have more time to explore the product.

Avg. Age: Younger generations that have used technology more and know how to use an Ipad better may make less complaints/service requests as they either troubleshoot online or find other methods to clarify their problems. Older generations that are not as well versed with technology may require more assistance or have more issues using the product, due to age compatibility.

Avg. Income (&#39;000s): Individuals with higher income levels may own an IPad or multiple IPads as compared to individuals from lower levels, as IPads can be considered luxury products, and thus this may affect number of complaints received.

Avg. Education (Yrs.): An individual with a higher education level may know how basic technology works better as they would have learnt basic computing skills and thus submit less complaints or they may problem solve better due to skills picked up through education, and could be predisposed to solve the issue using online/other resources.

Since seasonality was not detected, but the data is a time series, a normal regression could not be run to estimate the effect of help desk employees on number of constraints as leaving out variables would cause endogeneity problems. Thus, a dummy variable regression was conducted to account for both region and month. The disadvantage of using this model is that he R^2 may be massively inflated, which is why a within regression was also conducted.

Dummy variables were made using the first region and first month as a base, and control variables were added. The r^2 that was returned was extremely high at 0.9514 and can be due significant trends over time in the panel data. The coefficient of LogHelpDeskEmployees at         -2.9513 indicates that with every 1% increase in the level of involvement of help desk employees, there is a 2.9513% decrease in number of complaints received, ceteris paribus. At a p value of 0.00 this variable is significant in its effect on the number of complaints received. The regressions also indicate that some regions are significant at their p values are extremely low and the region can thus impact the number of complaints received, although not as heavily as the help desk employee level. Average worker hours per day, average income, average age and local employment were also significant, indicating that they each affect the number of complaints, ceteris paribus. Since the month variables do not significantly impact the number of complaints received in this model, and the variable was initially explored, it did not show seasonality but it showed significant variation. Thus, it is better to estimate the regression using fixed effects as the model eliminates omitted effects that are constant across time. [See appendix for regression model]

The fixed effects model includes all the control variables and clusters by region, making the fixed effects drop out of the equation, reducing endogeneity. This model gives a more reasonable r^2, although it is still significantly high at 0.9203, it is 0.0311 points lower than the r^2 returned by the dummy variable regression. The commands xtset and xtreg were used to estimate the model instead of using 5 separate commands to complete the same function.

The coefficient of LogHelpDeskEmployees at -2.9539 indicates that with every 1% increase in the level of involvement of help desk employees, there is a 2.9539% decrease in number of complaints received, ceteris paribus. This coefficient value is a 0.026 (absolute) increase in comparison to the coefficient of the dummy variable regression, which is not a very significant increase. An interesting observation is that all control variables excluding month and region are significant in this regression model with very low p values. Since this model makes assumptions about time trends and each month was an individual dummy and the variable showed variability (inconsistencies) it could not be replaced with a single t variable, making the FE model the best fit to estimate the relationship.

This model also helps reduce endogeneity as omitted effects across regions are eliminated by the process of the within estimator. However it is important to consider that omitted effects that vary across both are still present in the model and the model&#39;s accuracy can be improved if we have more data.

Recommendation

After observing the results from the various regression models, it was seen that the effect of the level of involvement of help desk employees is the most significant in reducing the number of complaints received. Apple Inc. could better train their employees to deal with customers that are older, have less experience with technology and maybe try to debug their OS in relation to reducing the number of complaints they receive. Regularly updating online help forums and increasing the level of help desk employees to do more such as reach out to customers who may have complained earlier or finding systems to faster evaluate common problems may help. Apart from employee training and caching, it may be helpful to take feedback from the employees and understand how to help them to keep customer satisfaction high in parallel to Apple&#39;s high product quality.


**Appendix 4: VBA Code to clean data**

Sub Clean()

    Dim sVariable As String

    Dim vEntry As Variant

    Dim iCounter As Integer

    Dim iCounter2 As Integer

    Dim iCounter3 As Integer

    Dim aiRecordLocator() As Integer

    Dim recCount As Integer

        For iCounter = 1 To 1734

      If Left(Sheets(&quot;Small Data&quot;).Range(&quot;A1&quot;).Offset(iCounter - 1, 0), 6) = &quot;Record&quot; Then

      recCount = recCount + 1

      ReDim Preserve aiRecordLocator(1 To recCount)

      aiRecordLocator(recCount) = iCounter

    End If

    Next iCounter

        For iCounter = 1 To 1734

        For iCounter2 = aiRecordLocator(iCounter) To (aiRecordLocator(iCounter + 1) - 2)

            For iCounter3 = 1 To (Sheets(&quot;Small Data&quot;).Range(&quot;A1&quot;).Offset(iCounter2, 1).End(xlToRight).Column - 1) Step 2

            sVariable = Sheets(&quot;Small Data&quot;).Range(&quot;A1&quot;).Offset(iCounter2, iCounter3)

            vEntry = Sheets(&quot;Small Data&quot;).Range(&quot;A1&quot;).Offset(iCounter2, iCounter3 + 1)

            If sVariable = &quot;Log of Help Desk Employees&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 0) = vEntry

            ElseIf sVariable = &quot;Log of Complaints&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 1) = vEntry

            ElseIf sVariable = &quot;Month&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 2) = vEntry

            ElseIf sVariable = &quot;Avg. Household Size&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 3) = vEntry

            ElseIf sVariable = &quot;Avg. Worker Hours (per day)&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 4) = vEntry

            ElseIf sVariable = &quot;Population (&#39;000s)&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 5) = vEntry

            ElseIf sVariable = &quot;Rainfall (Inches)&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 6) = vEntry

            ElseIf sVariable = &quot;Region&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 7) = vEntry

            ElseIf sVariable = &quot;Avg. Education (Yrs.)&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 8) = vEntry

            ElseIf sVariable = &quot;Local Unemployment&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 9) = vEntry

            ElseIf sVariable = &quot;Avg. Age&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 10) = vEntry

            ElseIf sVariable = &quot;Avg. Income (&#39;000s)&quot; Then

                Sheets(&quot;Sheet2&quot;).Range(&quot;A1&quot;).Offset(iCounter, 11) = vEntry

            End If

            Next iCounter3

        Next iCounter2

    Next iCounter

End Sub

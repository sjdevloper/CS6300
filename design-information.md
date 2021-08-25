
<h4>Team 98</h4> 
<h4>CS6300 Summer 2020</h4>  
<h4>Design Description Document</h4>  
This document captures the design description for Job Offer Comparison App based on the UML Class diagram provided as part of design.pdf file.
  
<h4> Design decisions</h4>  
Following design decisions made that are applicable throughout all the requirements:  
  
* GUI related functions are not expressed in the UML diagram. So, the description would just refer to it as a UI handler that takes care of UI related functions or activities.
* User could have zero or 1 current job.  
---
  
<h4>Requirements</h4>   

1. >When the app is started, the user is presented with the main menu, which allows the user to (1) enter current job details, (2) enter job offers, (3) adjust the comparison settings, or (4) compare job offers
(disabled if no job offers were entered yet).
  
	To realize this requirement, we’ve used the JobCompareSystem class as the entry point to the system or application. When the app is started, showMenuOptions() method would be invoked to display the main menu and the UI prompts will allow the user to enter current job details, job offers, adjust comparison settings and compare job offers.  
  
	Parallely, when the app is started, getJobDetails() method will be invoked which in turn would call getCurrentJob() method of CurrentJob class and getJobOffers() method of JobOffer class which in turn would call the parent Job class’ getJobDetails(isCurrentJob) to get both current job and offers if any stored in the system. The boolean attribute “isCurrentJob” associated with each job record can differentiate between current job(isCurrentJob = True) vs. job offers (isCurrentJob = False) records. If there are no JobOffer records retrieved (“isCurrentJob = False”), then the compare job offers menu will be disabled in the UI.
  
2.  > When choosing to enter current job details, a user will:
  - Be shown a user interface to enter (if it is the first time) or edit all of the details of their current job, which consist of:
  
	i. Title  
	ii. Company  
	iii. Location (entered as city and state)  
	iv. Overall cost of living in the location (expressed as an index)  
	v. Yearly salary  
	vi. Signing bonus  
	vii. Yearly bonus  
	viii. Retirement benefits (as percentage matched)  
	ix. Leave time (vacation days and holiday and/or sick leave, as a single overall number of days)   
  
	The UI handler as part of showMenuOptions() method will have the UI screen painted with all the above fields (Title, Company, Location, etc..) to interact with the user.  As explained in the previous requirement, the getJobDetails() method of the JobCompareSystem class would have retrieved all the job records that are stored in the system (Current Job and Job offers), when the app gets started. CurrentJob record can be identified using the boolean “isCurrentJob = True” attribute. If the CurrentJob record exists, corresponding details will be displayed on the UI screen accordingly and allowing the user to edit them. If not, the UI will have all the fields blank in the screen allowing the user to enter the details (since it would be the first time).  
  
- Be able to either save the job details or cancel and exit without saving, returning in both cases to the main menu.
	
	After providing the current job details, when the user clicks the save button, saveJobDetails() method will be called and the job details provided by the user will be associated with boolean attribute “isCurrentJob = True”. This method will in turn call addCurrentJob() method of CurrentJob class by passing the Job details entered by the user, which will save the job details in the system. The UI component will handle the actions where the user cancels or exits without saving and returning to the main menu.  
  
3. > When choosing to enter job offers, a user will:

- Be shown a user interface to enter all of the details of the offer, which are the same ones listed above for the current job.

	The UI handler as part of showMenuOptions() method will have the UI screen painted with all the above fields (Title, company, etc..) to interact with the user to have Job offer details entered which will be the same as that of for current job.  
	
- Be able to either save the job offer details or cancel.  
	
	After entering the job offer details, when the user clicks the save button, saveJobDetails() method will be called and the job details provided by the user will be associated with boolean attribute “isCurrentJob = False”. This method will in turn call addJobOffer() method of JobOffer class by passing the Job offer details entered by the user along with attribute “isCurrentJob = False” , which will in turn call the parent Job class to save the job offer details in the system.  
	
	The UI component will handle the actions related to user canceling and returning to the main menu.
	
- Be able to (1) enter another offer, (2) return to the main menu, or (3) compare the offer with the current job details (if present).  
	
	After entering Job offer details and saving them, the UI component will prompt the user whether he/she would like to add another job offer. If the user selects yes, the screen will be rendered to have the previous job offer values cleared and allowing the user to enter new job offer details.  
	
	The UI handler also provides the option for the user to return to the main menu by clicking the “Back to main menu” button.  
	
	As explained earlier,  getJobDetails() method would have already retrieved all job details (current vs job offers) if any from the system when the app is started. CurrentJob record can be identified using the boolean “isCurrentJob = True’ attribute. If the current job record exists, the UI will have a “Compare job” button enabled to provide an option to the user to compare job offer with current job details. If a current job record is not retrieved from the system, the “compare” button will be disabled or not shown in the UI screen.   
	
4. >When adjusting the comparison settings, the user can assign integer weights to:  
	i. Yearly salary  
	ii. Signing bonus  
	iii. Yearly bonus  
	iv. Retirement benefits  
	v. Leave time  
	If no weights are assigned, all factors are considered equal.  

	 The UI component will provide the option for user to enter weights related to all the factors listed above. Once the user clicks the “save/adjust compare settings” button, adjustComparisonSettings() of ComparisonSettings class will be invoked to store the factor weights.  
 
	If the user doesn’t provide any factor weights through the UI, then the weight attributes are assigned a default value of 1 in the ComparisonSettings class and all factors would have the same value and be considered equal.  
	
6.   >When choosing to compare job offers, a user will: 

 - Be shown a list of job offers, displayed as Title and Company, ranked from best to worst (see below for details), and including the current job (if present), clearly indicated.  
	
	When a user clicks on ‘Compare Job offers’ from the UI,  getJobDetails() method will be called which in turn will call getCurrentJob() and getJobOffers() method to get all the job records that are stored in the system. 
  
	Once retrieved, the UI component can rank the job records from best to worst based on the score attribute. The jobs would be listed as per the job score (best to worst) with a check box next to it. 
  
	The Job parent class while storing or adding any job record will also call the calculateJobScore()  method of JobScore utility class to calculate the score. Please refer to requirement 6 answer below for details.  

- Select two jobs to compare and trigger the comparison.
		
	User can select the check box next to the job list presented (best to worst) and click the ‘CompareJob’ button on the screen to 	initiate comparison.
		
-  Be shown a table comparing the two jobs, displaying, for each job:
		
	i. Title  
    	ii. Company  
   	iii. Location  
  	 iv. Yearly salary adjusted for cost of living  
   	 v. Signing bonus adjusted for cost of living  
  	 vi. Yearly bonus adjusted for cost of living  
  	vii. Retirement benefits (as percentage matched)  
 	viii. Leave time  
      
	The UI component will display the job attributes corresponding to the jobs chosen for comparison. The Yearly salary, signing bonus, yearly bonus values with adjusted cost of living is calculated by multiplying the attribute value with cost of living for the job location and the resulting value is displayed on the screen.  
  
-  Be offered to perform another comparison or go back to the main menu.  
		
	The UI handler will provide the option for the user to perform another comparison or go back to the main menu. If the user 		selects to perform another comparison, the job details would be displayed for comparison as explained in the second bullet.  
		
6.    >When ranking jobs, a job’s score is computed as the weighted sum of:  
		AYS + ASB + AYB + (RBP * AYS) + (LT * AYS / 260)  
		AYS = yearly salary adjusted for cost of living  
		ASB = signing bonus adjusted for cost of living  
		AYB = yearly bonus adjusted for cost of living  
		RBP = retirement benefits percentage  
		LT = leave time  
	
		For example, if the weights are 2 for the yearly salary, 2 for the retirement benefits, and 1 for all other factors, the score would be computed as:  

		2/7 * AYS + 1/7 * ASB + 1/7 * AYB + 2/7 * (RBP * AYS) + 1/7 * (LT * AYS / 260)  

		Job score calculation will be done for all job records that get stored in the Job class. This is done by invoking 		the calculateJobScore() method of the utility class JobScore by passing the AYS, ASB, RBP and AYB values. The method will call getComparisonSetting() method of ComparisonSettings class to get the weights corresponding to the factors and then use the formula provided above to calculate the job score and return it back to the caller.  
	
		*Note : AYS, ASB and AYB are calculated by having the original attribute values multiplied by Cost of living (index) provided by the user.*

6.  >The user interface must be intuitive and responsive.  

	This will be left out of the UML design because it is more of a physical representation on the GUI than it is on the UML class diagram. Intuitiveness and responsiveness can mean how one screen transitions to another, how the form is displayed, etc.   
7.   > The performance of the app should be such that users do not experience any considerable lag between their actions and the response of the app.  

		This requirement is left out of the UML class diagram because it is more about how the code will be written. This will be treated as a Non functional requirement.  
		
8.   > For simplicity, you may assume there is a single system running the app (no communication or saving between devices is necessary).

		The system is designed accordingly.


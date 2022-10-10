# loanapp-microservices
loanapp but microservices


Dear friend. This is a loan app. This loan app is an back-end application use to loan application. Loan application is used by custumer to apply small credit. Approved credit and amount is analize by user profile. The are some metrics used to profile analysis:

Occupation This metrics scored based on stability level. This metric has 30% ratio. This metrics has 5 ocupation main kind. So far there are PNS (5 points), BUMN (5 points), Swasta tetap (4 points), kontrak(2 points), and freelance (1 point)
Occupation long periode This metrics scored based on how long nasabah have been working. This metric has 20% ratio. point and score: Less than a year (1 points), 1-5 years (3 points), more than 5 years (5 points)
Ratio of angsuran to monthly income This metric scored based on how much loan payment will have impact to monthly income. This metric has 30% ratio. points and score: >50% (1 point), 30% to 50% (3 points), <30% (5 points)
Marriage status This metrics scored by how marriage status will have impact to nasabah monthly spend This metric has 30% ratio. points and score: single no child (4 points), single with chil (3 points), married no child (5 points), married with child (2 points)
Age This metrics scored by expected nasabah monthly income. Carrer start, seniority level, and expectedb retirement will impact thic scoring. This metric has 30% ratio. points and score: 16-25 yo (1 point), 26-35 yo (3 points), 36-55 yo(5 points), >55yo (1 point)
This scoring will be produce 5 max points. This point will be divided by 5 to get percentage final score. < 0.6 = reject 0.61 - 0.8 = considered with percentage max plafond. 0.8 = will get max plafond and proposed loan.

This backend application will run in port 8871 for loan service and 8872 for scoring services. Application need to acces database with localhost:3306/loanappdev.
Thic application need to access kafka at localhost:9092.

How this application run:

Start the application
Take a look at postman folder. Import collection
We need to create Nasabah data. Use nasabah/nasabahdataentry to input data nasbah. Data Nasabah is updateable. To get nasabah detail, use nasabah/nasabahdataget.
After nasabah created. We can input loan data. Use loan/loandataentry. Loan data is updateable as long as not submitted to scoring. To get data loan data, use loan/getloandata.
To submit loan data, use loan/submitloandata. This process is needed to going through scoring process.
After submit, it will send topic to kafka to trigger scroing service. In this process, submitted nasabah will be analyzed based on inputted profile.

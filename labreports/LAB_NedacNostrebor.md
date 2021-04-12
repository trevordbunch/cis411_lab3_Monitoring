# Lab Report: Monitoring
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Caden Robertson 
**GitHub Handle:** NedacNostrebor 
**Repository:** [Your Forked Repository](https://github.com/NedacNostrebor/cis411_lab5_Monitoring)
**Collaborators:** 
___

# Step 1: Fork this repository
- The URL of my forked repository
  - https://github.com/NedacNostrebor/cis411_lab5_Monitoring

# Step 2: Clone your forked repository from the command line
- My GraphQL response from adding myself as an account on the test project
```
{
  "data": {
    "mutateAccount": {
      "id": "5f3a540d-4812-454e-8fe3-8779e6c248f5",
      "name": "Caden Robertson",
      "email": "cr1350@messiah.edu"
    }
  }
}
```

# Step 3: Signup for and configure New Relic
- The chosen name of your New Relic ```app_name``` configuration
```
app_name: ['cislab']
```

# Step 4: Exercising the application / generating performance data

_Note: No lab notes required._

# Step 5: Explore your performance data
* What are your observations regarding the performance of this application? 
  > Queries take a lot longer to get than searching by tags. 
* Is performance even or uneven? 
  > Uneven
* Between queries and mutations, what requests are less performant? 
  > Queries take much longer
* Among the less performant requests, which ones are the most problematic?
  > Query 7 because it gives an error

# Step 6: Diagnosing an issue based on telemetry data
* Within the transactions you're examining, what segment(s) took the most time?
  > Query 6 took the most time
* Using New Relic, identify and record the least performant request(s).
  > Query 6 took the most time but post 7 had an error, so I guess that was the least performant
* Using the Transaction Trace capability in New Relic, identify which segment(s) in that request permeation is/are the most problematic and record your findings.
  > Remainder took up 95% of the duration
* Recommend a solution for improving the performance of those most problematic request(s) / permeation(s).
  > Search by bagel: everything rather than Query: everything so it doesn't have to look through each field for the word everything.

# Step 7: Submitting a Pull Request
_Note: No lab notes required._

# Step 8: [EXTRA CREDIT] Address the performance issue(s)
For the purposes of gaining 25% extra credit on the assignment, perform any of the following:
1. Adjust the diagnosed slow call(s) to improve performance. 
2. Verify the improved performance in New Relic, **including data and/or screenshots in your lab report**.
2. Check in those changes and **note your solution(s)** in your lab report.
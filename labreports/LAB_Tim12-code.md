# Lab Report: Monitoring
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Timothy Diana  
**GitHub Handle:** Tim12-code  
**Repository:** https://github.com/Tim12-code/cis411_lab5_Monitoring.git
**Collaborators:** @NedacNostrebor
___

# Step 1: Fork this repository
- https://github.com/trevordbunch/cis411_lab5_Monitoring

# Step 2: Clone your forked repository from the command line
{
  "data": {
    "mutateAccount": {
      "id": "40e0c90e-3f1a-4426-92ca-e630abf5eab4",
      "name": "Timothy Diana",
      "email": "td1245@messiah.edu"
    }
  }
}

# Step 3: Signup for and configure New Relic
- The chosen name of your New Relic ```cislab``` configuration
```
app_name: ['<cislab>']
```

# Step 4: Exercising the application / generating performance data
_Note: No lab notes required._

# Step 5: Explore your performance data
* What are your observations regarding the performance of this application? 
  > The app is quick besides some queries.
* Is performance even or uneven? 
  > Uneven
* Between queries and mutations, what requests are less performant? 
  > Queries take longer than mutations.
* Among the less performant requests, which ones are the most problematic?
  > The gmail.com query shows an error.

# Step 6: Diagnosing an issue based on telemetry data
* Within the transactions you're examining, what segment(s) took the most time?
  > The everything query took the longest.
* Using New Relic, identify and record the least performant request(s).
  > Query 6 and 7 (everything and gmail) were the lest performant. Query 6 took the longest, and query 7 had an error.
* Using the Transaction Trace capability in New Relic, identify which segment(s) in that request permeation is/are the most problematic and record your findings.
  > Remainder segment, it took up over 90% of the time.
* Recommend a solution for improving the performance of those most problematic request(s) / permeation(s).
  > Make queries more limited and be more precise on what information you want.

# Step 7: Submitting a Pull Request
_Note: No lab notes required._
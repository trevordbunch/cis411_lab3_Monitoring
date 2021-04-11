# Lab Report: Monitoring
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Joe Vera  
**GitHub Handle:** JoeV22  
**Repository:** [My Forked Repository](https://github.com/JoeV22/cis411_lab5_Monitoring)  
**Collaborators:** @trevordbunch @romansearle
___

# Step 1: Fork this repository
- The URL of my forked repository
- https://github.com/JoeV22/cis411_lab5_Monitoring

# Step 2: Clone your forked repository from the command line
- My GraphQL response from adding myself as an account on the test project
```
{
  "data": {
    "mutateAccount": {
      "id": "a10db030-ded8-4397-a78f-30b79d3497ab",
      "name": "MY NAME",
      "email": "MY EMAIL"
    }
  }
}
```

# Step 3: Signup for and configure New Relic
- The chosen name of your New Relic ```app_name``` configuration
```
app_name: ['<YOUR APP NAME>']
```

# Step 4: Exercising the application / generating performance data

_Note: No lab notes required._

# Step 5: Explore your performance data
* What are your observations regarding the performance of this application? 
  > The application is running well, it seems that most of the queries it handles rather quickly, however the last two it doesn't. The sixth query takes a while to produce results while the seventh throws an error message and stops.
  
* Is performance even or uneven? 
  > No the performance is not even. number 6 takes the most time, followed by number 1, it's a bit closer between 2,3,4,5 but 7 doesn't run it gives an error. So it is definately not even.
* Between queries and mutations, what requests are less performant? 
  > The less performant one was number 6 because it was requesting everything. 
* Among the less performant requests, which ones are the most problematic?
  > The seventh one was less performant because it crashed, while the sixth is a runner up because of how much time it took to run. The most problematic is the seventh run for crashing.

# Step 6: Diagnosing an issue based on telemetry data
* Within the transactions you're examining, what segment(s) took the most time?
  > the remainder was the transaction that took the most time.
* Using New Relic, identify and record the least performant request(s).
  > The least performant request was the seventh query that did not properly finish due to an error. The second least performant one was the sixth query that took a long time. It took in total 36,052 ms. The reason that the sixth query took the most was because of the request everything.
* Using the Transaction Trace capability in New Relic, identify which segment(s) in that request permeation is/are the most problematic and record your findings.
  >The most problematic one was the transactions where the remainder and loadOrderByID, taking 65% and 25% of the time respectively.
* Recommend a solution for improving the performance of those most problematic request(s) / permeation(s).
  > For the seventh query it seems that the errors are present throughout so it needs to be looked at again, the sixth query seems to have two id's, i think that we should check if thats really necessary because i think that's one of the reasons why it's taking a long time.

# Step 7: Submitting a Pull Request
_Note: No lab notes required._

# Step 8: [EXTRA CREDIT] Address the performance issue(s)
For the purposes of gaining 25% extra credit on the assignment, perform any of the following:
1. Adjust the diagnosed slow call(s) to improve performance. 
2. Verify the improved performance in New Relic, **including data and/or screenshots in your lab report**.
2. Check in those changes and **note your solution(s)** in your lab report.
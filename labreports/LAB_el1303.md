# Lab Report: Monitoring
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Emily Lopez  
**GitHub Handle:** el1303 
**Repository:**   el1303/cis411_lab5_Monitoring
**Collaborators:** 
___

# Step 1: Fork this repository
- [The URL of my forked repository](https://github.com/el1303/cis411_lab5_Monitoring)

# Step 2: Clone your forked repository from the command line
- My GraphQL response from adding myself as an account on the test project
```
{
  "data": {
    "mutateAccount": {
      "id": "a634942b-3395-4d9b-9fb6-dd04fca464c9",
      "name": "Emily Lopez",
      "email": "el1303@messiah.edu"
    }
  }
}
```

# Step 3: Signup for and configure New Relic
- The chosen name of your New Relic `cislab` configuration
```
app_name: ['<cislab>']
```

# Step 4: Exercising the application / generating performance data

_Note: No lab notes required._

# Step 5: Explore your performance data
* What are your observations regarding the performance of this application? 
  > My observation of the performance of this application is that the timing of the process of the analysis can be quick but slow also. One of them was so quick I didn't even know it ran.

* Is performance even or uneven? 
  > I’d say it’s uneven because it’s a hit or miss depending on what’s being done.

* Between queries and mutations, what requests are less performant? 
  > I’d say queries because the mutations are simple and get through fast. Queries actually process what’s being done and have to go through what's been inputted.

* Among the less performant requests, which ones are the most problematic?
  > The requests that are looking for a precise thing. They would have to search through and find what exactly they need.

# Step 6: Diagnosing an issue based on telemetry data
* Within the transactions you're examining, what segment(s) took the most time?
  > The section called remainder is what covers the graph bar the most showing that it takes more time. This was determined on noticing how the database has to look through each query to search through what's similar.

* Using New Relic, identify and record the least performant request(s).
  > For me query 6 took 29,483ms which was a lot more compared to the first one which was 2,939ms.
* Using the Transaction Trace capability in New Relic, identify which segment(s) in that request permeation is/are the most problematic and record your findings.
  > Query 6 showed remainder that took the longest because of it's running was 'everything'.
* Recommend a solution for improving the performance of those most problematic request(s) / permeation(s).
  > Not really sure how to make it improve by exact coding but I would thing similar to SQL instead of having to go through every single thing it would be easier to search for the specific bagel it's looking for and formatting it in that way.

# Step 7: Submitting a Pull Request
_Note: No lab notes required._

# Step 8: [EXTRA CREDIT] Address the performance issue(s)
For the purposes of gaining 25% extra credit on the assignment, perform any of the following:
1. Adjust the diagnosed slow call(s) to improve performance. 
2. Verify the improved performance in New Relic, **including data and/or screenshots in your lab report**.
2. Check in those changes and **note your solution(s)** in your lab report.
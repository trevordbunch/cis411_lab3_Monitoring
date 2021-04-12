# Lab Report: Monitoring
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Annika Kowalski  
**GitHub Handle:** AnnikaKowalski
**Repository:** https://github.com/AnnikaKowalski/cis411_lab5_Monitoring 
**Collaborators:** 
___

# Step 1: Fork this repository
  - This is the URL of my forked repository. https://github.com/AnnikaKowalski/cis411_lab5_Monitoring

# Step 2: Clone your forked repository from the command line
- My GraphQL response from adding myself as an account on the test project  
{  
  "data": {  
    "mutateAccount": {  
      "id": "5456e9a2-475b-4dee-96f4-8d22ca9b0709",  
      "name": "Annika Kowalski",  
      "email": "volleygirl21@comcast.net"      
    }  
  }    
}   
# Step 3: Signup for and configure New Relic
- The chosen name of your New Relic ```app_name``` configuration
```
app_name: ['cis411_Lab5']
```

# Step 4: Exercising the application / generating performance data

_Note: No lab notes required._

# Step 5: Explore your performance data
* What are your observations regarding the performance of this application? 
  - The performance of the application really relied on the what the query is. Some of the queries responded almost instantly while others took 30 seconds to over a minute to 
* Is performance even or uneven? 
  - As mentioned in the answer above the performance/response time was very scattered and unpredictable. With that being said the performance is very uneven. 
* Between queries and mutations, what requests are less performant? 
  - Queries are less performant. Queries have to search through all existing data which takes a lot of time and effort to perform. Some of the queries we were to perform gave me error messages which was challenging as well. Overall, mutations will not take longer than a mutation to perform.
* Among the less performant requests, which ones are the most problematic?
  - Queries are searching for specific strings of data which will make the performance of the query to take longer than other performances. When a query is being performed it goes through to check for the data each time it is run, as previously mentioned, which causes lag time as opposed to knowing which field/data to check first. 

# Step 6: Diagnosing an issue based on telemetry data
* Within the transactions you're examining, what segment(s) took the most time?
  - The query called "remainder took the most amount of time to return a response almost each time it was run. This took the most time because the server has to look through each database to find the ones that matched the query.
* Using New Relic, identify and record the least performant request(s).
  - Query #6 was the least performant query during the performance that I noticed. It took the longest to return any output which was about a minute to a minute and a half for a response. 
* Using the Transaction Trace capability in New Relic, identify which segment(s) in that request permeation is/are the most problematic and record your findings.
  - Once again Remainder was the one that took the longest amount of time to run. This took place because it was looking through each database for the term "everything."
* Recommend a solution for improving the performance of those most problematic request(s) / permeation(s).
  - Pulling everything in the database will always take the longest time since it is requiring so much searching to be done for everything not just a specific item. 

# Step 7: Submitting a Pull Request
_Note: No lab notes required._

# Step 8: [EXTRA CREDIT] Address the performance issue(s)
For the purposes of gaining 25% extra credit on the assignment, perform any of the following:
1. Adjust the diagnosed slow call(s) to improve performance. 
  - By changing the word query to bagel it drastically reduces the time it takes to get a response.
  {  
  #Query 6: retrieve all orders container the word everything  
  orders(bagel: "everything") {  
    id  
    customer {  
      id  
      email  
    }  
    items {  
      label  
      quantity  
    }  
  }  
}  

2. Verify the improved performance in New Relic, 
    - By making this change the time for a response went from almost a minute to roughly 4 seconds for a response. 
2. Check in those changes and in your lab report. 
    - The changes made were strictly to the working of the query not to the code.
# Lab Report: Monitoring
___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Hallie Nicholas  
**GitHub Handle:** hallienicholas  
**Repository:** [My Forked Repository](https://github.com/hallienicholas/cis411_lab5_Monitoring.git)  
**Collaborators:** 
 @JoeV22 @AnnikaKowalski
___

# Step 1: Fork this repository
- The URL of my forked repository is: https://github.com/hallienicholas/cis411_lab5_Monitoring.git

# Step 2: Clone your forked repository from the command line
- My GraphQL response from adding myself as an account on the test project
```
{
  "data": {
    "mutateAccount": {
      "id": "a84d4ba1-df1d-4f43-b27f-fa18eb6b46aa",
      "name": "Hallie Nicholas",
      "email": "hn1182@messiah.edu"
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

**Query 1 results:**
![Query 1](/assets/query1.png)

**Results after Query 2**
![Query 2](/assets/query2.png)

**Results after Query 3**
![Query 3](/assets/query3.png)

**Results after Query 4**
![Query 4](/assets/query4.png)

**Results after Query 5**
![Query 5](/assets/query5.png)

**Results after Query 6**
![Query 6](/assets/query6.png)

**Results after Query 7**
![Query 7](/assets/query7.png)

**Query 7 Response Time**
![Response Time](/assets/responsetime.png)

**Overview of all Transactions**
![Overview](/assets/overview.png)
![All past Transactions](/assets/transactions_all.png)

**Time Consumed By Segment**
![Time by Segment](/assets/bySegment.png)

# Step 5: Explore your performance data
* What are your observations regarding the performance of this application? 
  > According to what I have observed in this application, I can see that the response times for a majority of them were fairly steady except for a couple at the end. The only thing is that the queries all required different amounts of data and had differing response times, making the process a little choppy and uneven. The error at the end also stunted the deployment of this application.

* Is performance even or uneven? 
  > For this application, performance was uneven based on my observations. For each of the queries, when looking at throughput, which is the capacity of the app at each query, performance varies with each which can also be seen from the overview. The average throughput was 3.44 rpm but the queries are each anywhere from 0 to 25. Also, if you look at the average duration after each query, it is always different, some varying more than others between queries. This shows that the time during each is not linear; therefore, this app is not very consistent in it's performance. 

* Between queries and mutations, what requests are less performant? 
  > The requests that were less performant were query 6 and 7. With query 6, it took the longest amount of time to even show results for it, but it did better than 7 because it eventually had an output that wasn't an error. Query 7 showed an error as the output, and when looking at the dashboard on New Relic, the average duration for the transaction showed to be 526ms, which had jumped from only 153ms after query 6. Therefore, 6 and 7 definitely were the less perrformant ones for different reasons.

* Among the less performant requests, which ones are the most problematic?
  > The seventh query is the most problematic due to the error returned. This one also produced an error, so no helpful results were even given.

# Step 6: Diagnosing an issue based on telemetry data
* Within the transactions you're examining, what segment(s) took the most time?
  > The sixth query took the most time. Upon running, there is a considerably long response time compared to the other queries.
* Using New Relic, identify and record the least performant request(s).
  > The least performant request was the seventh. It resulted in an error saying that it could not validate the request, and could not query the field.
  ![Error](/assets/error.png)
* Using the Transaction Trace capability in New Relic, identify which segment(s) in that request permeation is/are the most problematic and record your findings.
  > The two worriesome requests throughout this lab have been the sixth and seventh. When looking at the Transaction Traces which are shown below for each, it seems that the seventh one had a longer response time at 45,000 ms while the sixth had response time of 41,300 ms. This surprised me because while I was running each, the sixth took much longer to produce an outcome than the seventh one. In addition, for both of them the "queryOrdersBySearchTerm" took the longest time other than "remainder". The remainder took a significant amount of time which makes me wonder if the database simply contains too much unnecessary data which showed specifically in 6. It was able to come up with a result, but with so much time that it might've taken extra to sort through all the other data that wasn't needed.

  **Transaction Trace for 6**
  ![Transaction Trace 6](/assets/6_transaction.png)

  **Transaction Trace for 7**
  ![Transaction Trace 7](/assets/responsetime.png)

* Recommend a solution for improving the performance of those most problematic request(s) / permeation(s).
  > The first thing I would suggest in order to improve performance would be to **remove unnecessary data** as I mentioned before. A big part of the response time could be that the program takes the query and needs to sort through information in the database that is not necessary and if some of that could be removed, response time could improve. Another thing that could be implemented is **cache control**. Cache control lowers the data load by reducing the amount of requests the system processes. This could potentially be good in this situation because cache control will stop the system from pulling resources that it has already used for previous queries. Therefore, GraphQL could access the history and, for example, if I had previously run the sixth query in this lab, the second time I run it I might get a shorter response time. It should be able to draw resources from running it the first time, thus improving the performance of the request. Another thing I might suggest trying is creating **indexes** within the database so that with each query, it wouldn't have to go through every single entry to look for the requested keywords or command, but instead just pull up a group of them using an ID. Looking at the Transaction Traces, it appeared that many, if not all, of the requests were slowed down due to "queryOrdersBySearchTerm". Therefore, if the data had been indexed, the system wouldn't have needed to spend that extra time searching for the search term, but could instead have a library of the terms together for easy access.
# Step 7: Submitting a Pull Request
_Note: No lab notes required._

# Step 8: [EXTRA CREDIT] Address the performance issue(s)
For the purposes of gaining 25% extra credit on the assignment, perform any of the following:
1. Adjust the diagnosed slow call(s) to improve performance. 
2. Verify the improved performance in New Relic, **including data and/or screenshots in your lab report**.
2. Check in those changes and **note your solution(s)** in your lab report.
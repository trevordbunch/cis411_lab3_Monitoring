# Lab Report: Monitoring

___
**Course:** CIS 411, Spring 2021  
**Instructor(s):** [Trevor Bunch](https://github.com/trevordbunch)  
**Name:** Micah Johnson  
**GitHub Handle:** @mcjo163  
**Repository:** [mcjo163/cis411_lab5_Monitoring](https://github.com/mcjo163/cis411_lab5_Monitoring)  
**Collaborators:** None
___

## Step 1: Fork this repository

[mcjo163/cis411_lab5_Monitoring](https://github.com/mcjo163/cis411_lab5_Monitoring)

## Step 2: Clone your forked repository from the command line

- My GraphQL response from adding myself as an account on the test project

```json
{
  "data": {
    "mutateAccount": {
      "id": "2cbf4966-0a9d-4e3e-85a1-2e899c6c5e75",
      "name": "MICAH JOHNSON",
      "email": "MJ1262@MESSIAH.EDU"
    }
  }
}
```

## Step 3: Signup for and configure New Relic

- The chosen name of your New Relic ```app_name``` configuration
  
```js
app_name: ['cislab5']
```

## Step 4: Exercising the application / generating performance data

_Note: No lab notes required._

## Step 5: Explore your performance data

- What are your observations regarding the performance of this application?
  > The performance seems to heavily depend on what the query is. Some queries returned almost instantly, and others took anywhere from 20 seconds to a minute.
- Is performance even or uneven?
  > Like I said above, it is uneven. It depends on what the query is looking for.
- Between queries and mutations, what requests are less performant?
  > Queries. They have to search through the existing database, rather than just adding onto it. Also, Query #7 has an error since it is asking for order-related fields from accounts. This is not the system's fault.
- Among the less performant requests, which ones are the most problematic?
  > The requests that are searching for a specific string in any data field take longer because all of the data fields have to be checked for each database item, rather than knowing which field to check.

## Step 6: Diagnosing an issue based on telemetry data

- Within the transactions you're examining, what segment(s) took the most time?
  > The segment called 'Remainder' almost always takes the most time. This was when the server had to look through each database item to find ones that match the query.
- Using New Relic, identify and record the least performant request(s).
  > Query #6 was the least performant. It took about a minute to return each time.
- Using the Transaction Trace capability in New Relic, identify which segment(s) in that request/permeation is/are the most problematic and record your findings.
  > Again it was the 'Remainder' segment that took the largest amount of time (about 51 seconds of the total 52 seconds), and this was when it was looking through every field of every database item for the string 'everything'.
- Recommend a solution for improving the performance of those most problematic request(s)/permeation(s).
  > Assuming the goal of Query #6 was to find orders that contained everything bagels, the query should be updated to use syntax similar to the raisin bagel query in Query #5. It may also be possible to improve the search algorithm used by the server, but I am not familiar enough with how it works to recommend anything specific there.

## Step 7: Submitting a Pull Request

_Note: No lab notes required._

## Step 8: [EXTRA CREDIT] Address the performance issue(s)

For the purposes of gaining 25% extra credit on the assignment, perform any of the following:

1. Adjust the diagnosed slow call(s) to improve performance.
   - I updated Query #6 as follows:

```graphql
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
```

2. Verify the improved performance in New Relic, **including data and/or screenshots in your lab report**.
   - Running this query instead of the original returns (likely the same) results in 0.4 seconds rather than 52 seconds.
   ![query improvement](/assets/extra_credit.png)
3. Check in those changes and **note your solution(s)** in your lab report.
   - I made no code changes, so I'm not sure if this is what you were looking for for this. But, it did dramatically improve the response time.

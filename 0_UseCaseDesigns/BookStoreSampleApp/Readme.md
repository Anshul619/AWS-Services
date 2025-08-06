# AWS BookStore Sample App

![](AWS-Bookstore-Demo-App.png)

# Tech Stack

| Service                                                                                                             | Remarks                                                                                      |
|---------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| [Amazon DynamoDB](../../1_Databases/AmazonDynamoDB/Readme.md)                   | It stores all of the data for books, orders, and the checkout cart.                          |
| [Amazon OpenSearch](../../1_Databases/AmazonOpenSearch/Readme.md)               | It powers search functionality for books.                                                    |
| [Amazon Neptune](../../1_Databases/AmazonNeptune.md)                            | It stores information on a user's social graph and book purchases to power recommendations.  |
| [Amazon ElasticCache for Redis](../../1_Databases/AmazonElasticCache/Readme.md) | It powers the books leaderboard.                                                             |
| [AWS Lambda](../../2_Compute/AWSLambda/Readme.md)                               | It updates derived data in different services like Amazon Elasticsearch, Amazon Neptune etc. |

# Read more
- [AWS bookstore sample app](https://github.com/aws-samples/aws-bookstore-demo-app)
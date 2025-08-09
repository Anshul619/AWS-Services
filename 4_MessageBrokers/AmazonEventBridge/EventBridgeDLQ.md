# Amazon Event Bridge DLQ

| Scenario                                | Will Event Go to DLQ? | Notes                                                                         |
|-----------------------------------------|-----------------------|-------------------------------------------------------------------------------|
| EventBridge cannot reach the target     | Yes                   | If DLQ is configured, after retries or immediately for non-retriable failures |
| Target (e.g. Lambda) executes but fails | No (EventBridge DLQ)  | Use Lambda’s own DLQ or error destination configuration instead               |

[Read more](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-rule-dlq.html)
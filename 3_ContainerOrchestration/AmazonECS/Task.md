# Task Definition
- A blueprint for our application and describes one or more containers through attributes.
- To prepare your application to run on [Amazon ECS](Readme.md), you create a task definition.
- The task definition is a text file, in JSON format, that describes one or more containers.
- A task definition is similar to a blueprint that describes the resources you need to run a container, such as CPU, memory, ports, images, storage, and networking information.

| Param                                                                                                               | Required for what launch type? (EC2 vs Fargate)       | Description                                                                                                                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Task Definition Name                                                                                                | Both                                                  | Name of task definition.                                                                                                                                                                                                                                                                           |
| [Task IAM Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html)                    | Both                                                  | [IAM Role](../../7_IdentityManagement/AWSIAM/Readme.md) that tasks can use to make API requests to authorized AWS resources                                                                                                                                                                         |
| [Task Execution IAM Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_execution_IAM_role.html) | Both                                                  | [This IAM role](../../7_IdentityManagement/AWSIAM/Readme.md) is required by tasks to pull container images and publish container logs to [Amazon Cloudwatch](../../8_ObservabilityLogs/AmazonCloudWatch/Readme.md) on our behalf.                                                           |
| Launch Type                                                                                                         | Both                                                  | Whether tasks are hosted on [Amazon EC2](../../2_Compute/AmazonEC2/Readme.md) or [Fargate](../../2_Compute/AWSFargate.md).                                                                                                                                                         |
| [Container Definitions](ContainerDefination.md)                                                                     | [Fargate only](../../2_Compute/AWSFargate.md) | [Docker image](https://github.com/Anshul619/HLD-System-Designs/blob/main/9_Container&Orchestration/Docker/Readme.md) to use with each container in your task. (Stored/Pulled from [Amazon ECR](../AmazonECR.md))                                                                                                                             |
| [Task Size (CPU & Memory)](https://docs.aws.amazon.com/AmazonECS/latest/bestpracticesguide/capacity-tasksize.html)  | [Fargate only](../../2_Compute/AWSFargate.md) | How much CPU and Memory to use for each task? <br/>- :star: [Container level memory settings](ContainerDefination.md) are optional when task size is set.<br/>- Task size is not supported for Windows containers.                                                                                 |
| [Networking Mode](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-networking.html)                 | Both                                                  | For [fargate](../../2_Compute/AWSFargate.md), we have only option available is AWS VPC in addition to [Docker Bridge](https://github.com/Anshul619/HLD-System-Designs/blob/main/9_Container&Orchestration/Docker/Readme.md), [Docker Host Only](https://github.com/Anshul619/HLD-System-Designs/blob/main/9_Container&Orchestration/Docker/Readme.md) & None networking modes. |
| [Logging Configuration](https://docs.aws.amazon.com/AmazonECS/latest/APIReference/API_LogConfiguration.html)        | Both                                                  |                                                                                                                                                                                                                                                                                                    |
| Others                                                                                                              |                                                       | Data Volumes etc.                                                                                                                                                                                                                                                                                  |

[Read more](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html)

# vCPU based quote for AWS Fargate tasks
- [AWS Fargate](../../2_Compute/AWSFargate.md) uses vCPU-based quotas, and it is important to ensure that you have the right value and limit set based on your scaling requirements.

# Example task definition

````json
{
  "family": "webserver",
  "containerDefinitions": [{
    "name": "web",
    "image": "nginx",
    "memory": "100",
    "cpu": "99"
  }],
  "requiresCompatibilities": ["FARGATE"],
  "networkMode": "awsvpc",
  "memory": "512",
  "cpu": "256"
}
````

# Amazon ECS task placement strategies

| Strategy   | Description                                                                                                                                                                                                                                     |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| binpack    | Tasks are placed on container instances so as to leave the least amount of unused CPU or memory. <br/>- This strategy minimizes the number of container instances in use.                                                                       |
| random     | Tasks are placed randomly.                                                                                                                                                                                                                      |
| spread     | Tasks are placed evenly based on the specified value. Accepted values are instanceId (or host, which has the same effect), or any platform or custom attribute that's applied to a container instance, such as attribute:ecs.availability-zone. |

[Read more](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement-strategies.html)

# Amazon ECS placement constraints

| Constraint         | Description                                                                                                                                              |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| distinctInstance   | Place each task on a different container instance. This task placement constraint can be specified when either running a task or creating a new service. |
| memberOf           | Place tasks on container instances that satisfy an expression.                                                                                           |
| ecs.os-family      | LINUX or WINDOWS_SERVER_<OS_Release>_<FULL or CORE>.                                                                                                     |

[Read more](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement-constraints.html)

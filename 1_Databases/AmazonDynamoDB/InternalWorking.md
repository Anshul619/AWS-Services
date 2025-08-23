# How DynamoDB works?
- They do consistent hashing to partition data
- They use virtual nodes to avoid hot shards
- They replicate data across many servers for durability
- They use sloppy quorum for data consistency
- They use vector clocks to find the latest data version
- They allow the client logic to resolve data conflicts
- They use hinted handoff to handle temporary failures
- They use Merkle trees to synchronize servers and handle permanent failures
- They use gossip protocol for service discovery and failure detection
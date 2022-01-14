# Optimistic Concurrency

## Notes

**Optimistic concurrency** - If and when the API server detects concurrent write attempts, it rejects the latter of the two write operations. It is then up to the client to handle a conflict and potentially retry the write operation.

Conflict errors are totally normal in controllers. Always expect them and handle them gracefully.

Optimistic concurrency is a perfect fit for level-based logic, because by using level-based logic you can just rerun the control loop. Another run of that loop will automatically undo optimistic changes from the previous failed optimistic attempt, and it will try to update the world to the latest state.

{% embed url="https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/optimistic-concurrency" %}

## FAQ


# Optimistic Concurrency

## Notes

If and when the API server detects concurrent write attempts, it rejects the latter of the two write operations. It is then up to the client to handle a conflict and potentially retry the write operation.

Conflict errors are totally normal in controllers. Always expect them and handle them gracefully.

Optimistic concurrency is a perfect fit for level-based logic.

{% embed url="https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/optimistic-concurrency" %}

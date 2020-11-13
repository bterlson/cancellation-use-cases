## A worker in the cloud

Nodes in a distributed cloud application come and go. A common way to tell a node that its job is done is to send it SIGINT. The node will then do any cleanup necessary to ensure the application is left in a good state.

Distributed cloud applications do many operations in an asynchronous fashion which need to be responsive to additional input from users or other processes. It is common for work to begin optimistically only to realize it's no longer needed.

In these cases, cancellation is handy - application and library code doesn't need to worry about each individual source of cancellation, whether the process is going down, new user input came in, the data is no longer needed, or a timeout occurred. It simply handles the signal by doing any necessary cleanup and state rationalization.

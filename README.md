High-level approach:
We looked at the Raft Paper and used the implementation startegy provided in the project description. We first tried to implement the leader election. And after doing that sucessfully, wem moved on to the Append Entries for followers. Then we implemented how the leader will respond top the appendResponses from the follower. After implementing this, we moved on to the commit portion of the protocol. In this we check we have the majority rpelicas ready to commit, and if so the leader sent out the commit message. We also have functionality to check the log consistency among followers. We look at the index of the follower's log which matches the leader log  and send the log after that to follower. 

Challenges you faced:
As we tested under different circumstances, we needed to modify our code to compile with the test cases. A large part of the challenge we faced was to make the replicas store states and respond to PUT requests. A huge part of the project was to understand the raft protocol and make sure we have implemented all the components of it so that the replicas can replicate the leader's messages, update their own logs, and store them in the state machine accordingly. 

Properties/features:
We abstracted functionalities into helper functions, which makes the structure of our code more concise and easier to debug. The way we are handling messages is based on the status of the replica, so we had follower_message, candidate_message, and leader_message. Then we implemented the corresponding responsibility for each type of message handling. 

Testing:
We used logging and print statements throughout the project to easily see which messages were received and sent to followers and how the followers repsond to it. We also used test scripts provided by the starter code, which tested the performance of our program under different circumstances. 
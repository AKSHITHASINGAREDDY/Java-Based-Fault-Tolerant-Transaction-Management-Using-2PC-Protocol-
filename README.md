# Java-Based-Fault-Tolerant-Transaction-Management-Using-2PC-Protocol-
Developed and tested a Java-based distributed transaction management system using the 2-Phase Commit (2PC) protocol, successfully demonstrating fault tolerance and recovery in scenarios involving coordinator and node failures. 

## how to execute 
1.TC FAILURE:

  1.Manager :To execute javac Manager2.java and to run java Manager2
  
  2.Process1:To execute javac Process1.java and to run java Process1
  
  3.Process2:To execute javac Process2.java and to run java Process2
  
  4.Process3:To execute javac Process3.java and to run java Process3
  
  5.Run all the four terminals
  
  6.stop the coordinator before prepare voting
  
  7.run it again after time out
  
2.NODE FAILURE: 
  
  1.Manager :To execute javac Manager2.java and to run java Manager2
  
  2.Process1:To execute javac Process1.java and to run java Process1
  
  3.Process2:To execute javac Process2.java and to run java Process2
  
  4.Process3:To execute javac Process3.java and to run java Process3
  
  5.Run all the four terminals
  
  6.stop the process1 before yes
  
3.TC FAILURE:
 
  1.Manager :To execute javac Manager2.java and to run java Manager2
  
  2.Process1:To execute javac Process1.java and to run java Process1
  
  3.Process2:To execute javac Process2.java and to run java Process2
  
  4.Process3:To execute javac Process3.java and to run java Process3
  
  5.Run all the four terminals
  
  6.stop the coordinator after we get one commit message
  
  7.run the coordinator after time out
  
4.NODE FAILURE:
  
  1.Manager :To execute javac Manager2.java and to run java Manager2
  
  2.Process1:To execute javac Process1.java and to run java Process1
  
  3.Process2:To execute javac Process2.java and to run java Process2
  
  4.Process3:To execute javac Process3.java and to run java Process3
  
  5.Run all the four terminals
  
  6.stop the process after we have all yes and get one commit message
  
  7.run the process after time out
  
  ## Explanation of different scenarios
01. TC failure:  
If the coordinator fails before sending the "prepare" message, nodes will not receive the "prepare" message until the time-out and will abort. So, they will respond "no" to the "prepare" message after the coordinator comes back up and sends the "prepare" message.
The first failure scenario involves the TC failing before sending the "prepare" message. In this case, participants will not receive the "prepare" message until the time-out and will abort. When the TC comes back up, it sends the "prepare" message again, and participants respond with "no" since they have already aborted.

02. Node failure:
  
If the transaction coordinator does not receive "yes" from a node, it will abort the transaction.
The second failure scenario involves a node failing to send a "yes" message to the TC during the prepare phase. In this case, the TC aborts the transaction since it did not receive a "yes" message from all participants

03. TC failure:
   
TC needs to store the transaction information on disk before sending the "commit" message to the nodes. If the TC fails after sending one "commit" message to the nodes, it can't abort. When it comes back up it will send the "commit" message to the nodes that it didn't send the "commit" message to.
The third failure scenario involves the TC failing after sending one "commit" message to the nodes. In this case, the TC cannot abort and, when it comes back up, sends the "commit" message to the remaining nodes that it did not send the message to earlier.

04. Node failure:  
A node needs to store the transaction information before replying "yes" to the TC. If it fails (time-out) after replying "yes"; after it comes back up, it will fetch the commit information from the TC for that particular transaction.
The fourth failure scenario involves a node failing after replying "yes" to the TC during the prepare phase. In this case, when the node comes back up, it fetches the commit information from the TC for that particular transaction.
To emulate a failure, a much longer delay is imposed at a failed node than the time-out period used by other active nodes. The node prints its state (commit/abort) before termination. The goal of this exercise is to study how the 2PC protocol handles different types of failures and to evaluate the effectiveness of the time-out mechanism and the protocol's fault-tolerance capabilities.




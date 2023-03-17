# Practical Session #1: Introduction

1. Find in news sources a general public article reporting the discovery of a software bug. Describe the bug. If possible, say whether the bug is local or global and describe the failure that manifested its presence. Explain the repercussions of the bug for clients/consumers and the company or entity behind the faulty program. Speculate whether, in your opinion, testing the right scenario would have helped to discover the fault.



2. Apache Commons projects are known for the quality of their code and development practices. They use dedicated issue tracking systems to discuss and follow the evolution of bugs and new features. The following link https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-794?filter=doneissues points to the issues considered as solved for the Apache Commons Collections project. Among those issues find one that corresponds to a bug that has been solved. Classify the bug as local or global. Explain the bug and the solution. Did the contributors of the project add new tests to ensure that the bug is detected if it reappears in the future?

3. Netflix is famous, among other things we love, for the popularization of *Chaos Engineering*, a fault-tolerance verification technique. The company has implemented protocols to test their entire system in production by simulating faults such as a server shutdown. During these experiments they evaluate the system's capabilities of delivering content under different conditions. The technique was described in [a paper](https://arxiv.org/ftp/arxiv/papers/1702/1702.05843.pdf) published in 2016. Read the paper and briefly explain what are the concrete experiments they perform, what are the requirements for these experiments, what are the variables they observe and what are the main results they obtained. Is Netflix the only company performing these experiments? Speculate how these experiments could be carried in other organizations in terms of the kind of experiment that could be performed and the system variables to observe during the experiments.

4. [WebAssembly](https://webassembly.org/) has become the fourth official language supported by web browsers. The language was born from a joint effort of the major players in the Web. Its creators presented their design decisions and the formal specification in [a scientific paper](https://people.mpi-sws.org/~rossberg/papers/Haas,%20Rossberg,%20Schuff,%20Titzer,%20Gohman,%20Wagner,%20Zakai,%20Bastien,%20Holman%20-%20Bringing%20the%20Web%20up%20to%20Speed%20with%20WebAssembly.pdf) published in 2018. The goal of the language is to be a low level, safe and portable compilation target for the Web and other embedding environments. The authors say that it is the first industrial strength language designed with formal semantics from the start. This evidences the feasibility of constructive approaches in this area. Read the paper and explain what are the main advantages of having a formal specification for WebAssembly. In your opinion, does this mean that WebAssembly implementations should not be tested? 

5.  Shortly after the appearance of WebAssembly another paper proposed a mechanized specification of the language using Isabelle. The paper can be consulted here: https://www.cl.cam.ac.uk/~caw77/papers/mechanising-and-verifying-the-webassembly-specification.pdf. This mechanized specification complements the first formalization attempt from the paper. According to the author of this second paper, what are the main advantages of the mechanized specification? Did it help improving the original formal specification of the language? What other artifacts were derived from this mechanized specification? How did the author verify the specification? Does this new specification removes the need for testing?

## Answers

1) An exemple of a local bug : The Dhahran missile. It was an antiballistic system that failed to launch because of a bug. The system was supposed to launch a missile to intercept an enemy projectile, but the problem was that the internal clock drifted by a couple of milliseconds every hour, leading to a delay of 0,3 seconds after 100 hours. This delay translated into a difference of 600 meters for tracking enemy projectile, making the system inffective. In 1991 a missile hit an US base causing 28 death, the antiballistic system didn't responded, revealing this bug. More intense testing would have prevented this incident.

----

2)
https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-814?filter=doneissues

This issue is a local bug.
This bug is caused because the behaviour of exception throw by Java was not properly understood. An NPE is thrown when the 1st parameter is empty, not when the 2nd parameter is null.
The solution was to change the test case to correspond to the specification.




----
3)
Concrete experiments they performed :   
    -  Chaos Monkey : randomly terminates virtual machine instances that host production services to encourage engineers to design software services that can withstand such failures.  
    - Chaos Kong : simulates the failure of an entire Amazon EC2 region.  
    - Failure Injection Testing (FIT) : exercises where they intentionally cause requests between Netflix services to fail and verify that the system degrades gracefully.  
Requirements for these experiments :  
    - formulate a hypothesis about how the system will behave under certain conditions  
    - define what a normal behavior is and what an abnormal one is  
    - be able to measure impact of events in the system  
    - run experiment directly in production  
    - automate experiments  
    - minimize impacts of failures  
Variables they observed :  
    - number of requests that were affected  
    - the impact on availability and latency  
    - number of requests that were successfully handled  
Main results :  
    - successfully improving reliability of Netflix’s systems with production conditions  
    
These experiments could be done with trains. We could for example observe the vibrations of a train when it travels on a real terrain.

----

4.

 The main advantages of having a formal specification for WebAssembly :  
 - it helps developers write better programs as when you know exactly how the language works, you can make sure your programs will run smoothly without any surprises.  
 - different web browsers can more easaly work together and run WebAssembly programs consistently. That means programms can work well on any browser, without having to worry about compatibility issues.  
WebAssembly implementations should be tested because the behavior of the programm may deviate from the client's vision.
----

5) According to the author of this paper, they were able to identify and fix some bugs and errors from the official WebAssembly specification. They were also able to prove the safety of the type system.
   This makes the mechanized specification way more trustable and very effective. The problem is that it is only applicable on a restricted scale, not making the use of tests unnecessary.


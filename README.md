# TimedEventB
The plugin **TimedEventB** permits to specify timing properties on Event-B models. These properties are mainly attached to tasks represented as Event-B events. For that purpose, we distinguish two task types:

1. Atomic tasks: these tasks are instantaneous and do not take time to complete.
2. Non atomic tasks: these tasks are not instantaneous and have duration.

To create a task using our plugin, click on the  button **Te**. Then select its type . 
   <img width="1234" height="508" alt="createTak" src="https://github.com/user-attachments/assets/a3adc51b-4c04-406c-95dc-98c3c58f1330" />

**Case of an atomic task**: the creation of an atomic task produces the following Event-B specificaition. To deal with timing properties, a master variable _CK_ along with a _Progress_ event are defined. This event makes time progress by a given non null amont of time _Step_. Of course, the master varaible and the associated event are created once while creating the first task.

   <img width="988" height="699" alt="atomicTask" src="https://github.com/user-attachments/assets/fbf52dbc-b290-45f4-927b-56c019835d4b" />

For each task _A_, we have  a variable _Scheduler_A_ which denotes an increasing sequence of value pairs (_start_, _end_) for each  execution of the task _A_. An atomic task  _A_ is represented by a unique event _Atomic_A_. Event _Atomic_A_has the follwowing implicit guard/action:

guard: CK > last(_Scheduler_A_) //to ensure that two different instances of the task _A_ do not occur at the same time

action: _Scheduler_A_:=_Append_(_Append_(_Scheduler_A_, _CK_), _CK_)//Append denotes the append operation of sequences

On an atomic task, a min/max timing periodicity constraint my be defined. The periodicity constraint denotes the min/max amount of time that separates the begining of two 
conseuctive instances. This constraint induces the following implicit guard: 

guard_per: Scheduler_A /= {} CK - BefLast(Scheduler_A) >=/<= PSMin/PSMax //BefLast(Scheduler_A) denotes the before last element of the sequence _Scheduler_A_.
  

Depnding on the type of a task, 

We distinguish two timing property kinds:
1. Mono-task properties: these properties include _duration_, _periodicity_ and _speration. 
2. Bi-task properties: these properties mainly denote ordering properties like _followed _and _preceded.

   
   a. **Duration**:  To create a task, click on the  button **Te**. Then select _Non atomic task. 
   <img width="1234" height="508" alt="createTak" src="https://github.com/user-attachments/assets/a3adc51b-4c04-406c-95dc-98c3c58f1330" />

  This produces the following Event-B specification:
  
   <img width="1294" height="721" alt="taskDuration" src="https://github.com/user-attachments/assets/b1e51e2a-67d2-4145-9540-5b6632191e74" />

   To deal with timing properties, a master variable _CK_ along with a Progress event are defined. This event makes time progress by a given non null amont of time _step. Of course, the master varaible and the associated event are created once while creating the first task.
   
   With a task _A_, the following elements are associated:

   (_i_)  a variable _Scheduler_A_which denotes an increasing sequances of value pairs (_start_, _end_) for each  execution of the task _A.
   
   (_ii_)_as the task _A _ has a duration, two event _start_A__ and __end_A_. As one can see, the _duration_ property is attached to the end event while the seperation and periodicity one are associated with the start event. For each property, users can specify mimimun/maximum values.
   
   

   
   

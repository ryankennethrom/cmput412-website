# Exercise 2 Report

#### What is a ROS node, and what is its role in the ROS ecosystem ?

Ros is a distributed framework of processes (aka Nodes) that enables executables to be individually designed and loosely coupled at runtime. 

A package may contain ROS runtime processes (nodes).

Nodes are processes that perform computation. Ros is designed to be modular at a fined-grained scale; a robot control system usually comprises many nodes. For example, one node controls a laser range-finder, one node controls the wheel motors, one node performs localization, one node performs path planning, one Node provides a graphical view of the system, and so on. A ROS node is written with the use of a ROS client library, such as roscpp or rospy.

#### What are ROS topics, and how do they facilitate communication between nodes ?

Messages are routed via a transport system with publish / subscribe semantics. A node sends out a message by publishing it to a given topic. The topic is a name that is used to identify the content of the message. A node that is interested in a certain kind of data will subcribe to the appropriate topic. There may be multiple concurrent publishers and subscribers for a single topic, and a single node may publish and/or subscribe to multiple topics. In general, publishers and subscribers are not aware of each other's existence. The ideas is to decouple the production of information from its consumption. Logically, one can think of a topic as a strongly typed message bus. Each bus has a name, and anyone can connect to the bus to send or receive messages as long as they are the right type.

#### What are ROS services, and how do they differ from topics ?

Service descriptions, stored in my_package/srv/MyServiceType.srv, define the request and response data structures for messages sent in ROS.

The publish / subscribe model is a very flexible communication paradigm, but its many-to-many
, one-way transport is not appropriate for request / reply interactions, which are often required in a distributed system. Request / reply is done via services, which are defined by a pair of message structures: one for the request and one for the reply. A providing node offers a service under a name and a client uses the service by sending the request message and awaiting the reply. ROS client libraries generally present this interaction to the programmer as if it were a remote procedure call.

#### What are ROS messages, and how are they structured for communication ?

Message descriptions, stored in my_package/msg/MyMessageType.msg, define the data structures for messages sent in ROS.

Nodes communicate with each other by passing messages. A message is simply a data structure, comprising typed fields. Standard primitive types (integer, floating point, boolean, etc.) are supported, as are arrays of primitive types. Messages can include arbitrarily nested structures and arrays (much like C structs).

#### What is a ROS bag, and how is it used in data recording and playback ?

Bags are a format for saving and playing back ROS message data. Bags are an important mechanism for storing data, such as sensor data, that can be difficult to collect but is necessary for developing and testing algorithms.

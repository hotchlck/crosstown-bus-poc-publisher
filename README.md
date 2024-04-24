# Modul 8 Reflection
**Salma Kurnia Dewi (2206026681)**

## How many data your publisher program will send to the message broker in one run?
   In the ```main.rs``` file in the publisher folder, there are 5 calls to the ```publish_event(...)``` method. Each call sends a ```UserCreatedEventMessage``` as its parameter.
   There is no looping in this program, so in one run, there will only be 5 calls to the ```publish_event(...)``` method. Therefore, the publisher program will send 5 data to the message broker in one run. 
   This can also be seen from the number of commands ```_ = p.publish_event("user_created".to_owned(), UserCreatedEventMessage { user_id: "1".to_owned(), user_name: "2206026681-Amir".to_owned() });``` in the program. So, in one run, there will be 5 data sent to the message broker.

## The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
   Both the subscriber and publisher programs are connected to a single AMQP server with the URL ```amqp://guest:guest@localhost:5672```, which is used to create a new publisher queue. 
   This server has a username ```guest``` and password ```guest```, and the hostname of the machine where the broker runs is localhost. 
    The AMQP broker keeps track of connections on port number ```5672```. If the URL on the publisher and subscriber is the same, it indicates that they are connected to the same server for message exchange. 
    he purpose of this setup is to ensure that messages published by the publisher can be received and processed by the subscriber, thereby facilitating efficient and effective communication between them.

## Running RabitMQ as message broker 
<img src = "img/RabbitMQ.png"> 

## Sending and Processing Event
<img src = "img/pub&sub.png">

When we execute the ```cargo run``` command on the publisher and subscriber, the following process occurs: The publisher sends data to the message broker (RabbitMQ), which then forwards it to the subscriber. 
The subscriber receives and processes this data according to the information received. This process can be seen from the provided console screenshot. 
More specifically, when I execute the ```cargo run``` command on the subscriber and publisher, the publisher sends 5 events to the message broker.
These events are then received and processed by the publisher. Thus, both images demonstrate the interaction process between the publisher, message broker, and subscriber in this system.

## Monitoring chart based on publisher
<img src = "img/spikes.png">

In the displayed graph visualization, there are two significant spikes in the ‘message rates last minute’ graph when I executed the ```cargo run``` command twice in the publisher directory. These spikes in the graph represent the number of messages received by the subscriber in the last minute. The intensity of these spikes is directly proportional to the number of messages: the more messages received, the higher the spike. 
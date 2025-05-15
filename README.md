## How much data your publisher program will send to the message broker in one run? 

My publisher program sends five messages to the message broker in one run. Each message is an instance of UserCreatedEventMessage, having a user_id and a user_name. The total data sent is the sum of the serialized sizes of these five messages. Since each message contains two short strings, the total data is being sent to the broker is not a lot. The publisher sends these messages by calling publish_event five times, each with different user data.

## The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

The URL “amqp://guest:guest@localhost:5672” in the publisher program specifies the connection details for the message broker. If the subscriber program uses the same URL, it means both the publisher and subscriber are connecting to the same message broker instance running locally on my machine (localhost) at port 5672, with username “guest” and password “guest.” This shared connection means the publisher can send messages to the broker, and the subscriber can receive those messages.



## How much data your publisher program will send to the message broker in one run? 

My publisher program sends five messages to the message broker in one run. Each message is an instance of UserCreatedEventMessage, having a user_id and a user_name. The total data sent is the sum of the serialized sizes of these five messages. Since each message contains two short strings, the total data is being sent to the broker is not a lot. The publisher sends these messages by calling publish_event five times, each with different user data.

## The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

The URL “amqp://guest:guest@localhost:5672” in the publisher program specifies the connection details for the message broker. If the subscriber program uses the same URL, it means both the publisher and subscriber are connecting to the same message broker instance running locally on my machine (localhost) at port 5672, with username “guest” and password “guest.” This shared connection means the publisher can send messages to the broker, and the subscriber can receive those messages.

![image](https://github.com/user-attachments/assets/5082916b-cab1-43d4-ba12-391f9f970931)

![image](https://github.com/user-attachments/assets/6bd87531-90fa-4901-85b3-08ca247e4440)
![image](https://github.com/user-attachments/assets/8fe931bc-cd25-48e4-88dc-a84c03812b09)
When I run `cargo run` in publisher, it connects to the RabbitMQ message broker and sends five `UserCreatedEventMessage` messages, each with a different user, to the `user_created` queue. When I run the subscriber folder, it connects to the same RabbitMQ broker, listens to the `user_created` queue, and prints out each message it receives. As a result, every time the publisher sends messages, the subscriber receives and displays them, showing the user information for each event.

![image](https://github.com/user-attachments/assets/01a8db6c-002e-4129-a135-ffca10a39925)
The graph shows the message rates per minute as spikes in the charts, so in the first spike, I ran `cargo run` three times in quick succession, and then the secocnd spike is lower because I only ran that command one more time.

### Microservice Architecture
Applying this architecture to an application that will convert video files to MP3 files. 

#### Python, RabbitMQ, mongoDB, Docker, Kubernetes, MySQL

- When a user uploads a video to be converted to MP3 that request will first hit our Gateway.
- Gateway will then store the video in mongodb and then put a message on the queue - RabbitMQ queue (letting Downstream Services know that there is a video to be processed in mongodb)
- The video to MP3 converter service will consume messages from the queue.
- It will then get the ID of the video from the message, pull that video from mongodb, convert the video to MP3, then store the MP3 on mongodb
- Then put a new message on the Queue to be consumed by the notification service that says that the conversion job is done.
- The notification service consumes those messages from the queue and sends an email notification to the client informing the client that the MP3 for the video that he or she uploaded is ready for download.
- The client will then use a unique ID acquired from the notification education and his or her JWT to make a request to the API Gateway to download the MP3
- The API Gateway will pull the MP3 from mongodb and serve it to the client
- This is the overall conversion flow and how RabbitMQ is integrated with the overall system.

#### Installations

- Docker : https://docs.docker.com/get-docker/
- Kubernetes (kubectl) : https://kubernetes.io/docs/tasks/tools/
- minikube : https://minikube.sigs.k8s.io/docs/start/
- k9s : https://community.chocolatey.org/packages/k9s
- Python (version 3+)
- MySQL





 

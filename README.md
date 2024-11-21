# w12_go_1

```bash
docker build -t dw11:0.1 .
docker run -p 80:80 dw11:0.1
docker run -p 80:80 dw11:0.1
git add .
git commit -m "update"
git push -u origin master 
go test
go test -v
go test -v -run TestFileServer
go test ./...

docker run -d --name mongodb -p 27017:27017 -v mongo-data:/data/db mongo

```

# **Command Breakdown**
docker run:
- Creates and runs a new container.
-d:
- Runs the container in detached mode (in the background).
--name mongodb:
- Assigns the name mongodb to the container for easy identification.
-p 27017:27017:
- Maps port 27017 on the host machine to port 27017 inside the container, which is MongoDB's default port. This allows you to access MongoDB on localhost:27017.
-v mongo-data:/data/db:
- Mounts a Docker volume named mongo-data to the /data/db directory inside the container. The /data/db directory is where MongoDB stores its data. This ensures that the data persists even if the container is removed or stopped.
mongo:
- Specifies the Docker image to use. In this case, the official MongoDB image.

---
Your script sends the user's public IP address (obtained via the https://api.ipify.org API) to your local server at http://localhost/api/visitors. Here's an analysis of how it works, its purpose, and a few tips for improvement.
<script>
        fetch('https://api.ipify.org?format=json')
            .then(response => response.json()) 
- This fetches the public IP address of the user and parses the response JSON to extract the ip value.
            .then(data => {
                fetch('http://localhost/api/visitors', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({ ip: data.ip }),
                });
            })
 - Sends the IP address to a local server endpoint using a POST request with a JSON payload.
            .catch(error => console.error('Error:', error));
- Captures and logs any errors during the fetch operations.
    </script>
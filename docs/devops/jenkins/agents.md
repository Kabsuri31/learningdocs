
<h3>Jenkins communication protocols</h3>

In Jenkins, worker nodes (agents) communicate with the Jenkins master (controller) to execute jobs. There are two main protocols used to facilitate this communication:

1. <b>JNLP (Java Network Launch Protocol)</b>

JNLP agents are typically used when the agent is outside the same network as the Jenkins master or if it cannot establish direct communication.

How it works:

The agent connects outbound to the Jenkins master using JNLP over TCP.
The connection avoids firewall issues since the worker initiates the connection.
JNLP agents require a secret key/token for authentication, available from the Jenkins UI.
Setup:

The agent needs the slave.jar file.
Example command to connect:
bash
Copy code

java -jar agent.jar -jnlpUrl http://<jenkins_url>/computer/<agent_name>/slave-agent.jnlp -secret <secret>

Use Case: Ideal for dynamic or cloud-based agents like AWS or Kubernetes.

<br>
2. <b>WebSocket Communication</b>

In newer Jenkins versions, agents and the controller can communicate via WebSocket. This helps when direct TCP connections are blocked by proxies or firewalls.

How it works:
Jenkins can initiate a WebSocket connection through HTTP or HTTPS.
This is a persistent connection over the web, suitable for scenarios where outbound traffic must pass through a proxy.
Use Case:

Often used in containerized environments (like Kubernetes) or where firewalls restrict other protocols.

<br>
3. <b>SSH Agents</b>

For agents on the same or trusted networks, Jenkins can also use SSH to communicate.

How it works:
Jenkins master initiates an SSH connection to the agent.
SSH credentials or keys are configured in Jenkins for secure authentication.
Once connected, the agent listens for tasks to execute.
Use Case:

Good for static worker nodes in a secure, internal network.
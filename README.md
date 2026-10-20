# Jenkins Remoting Project

## Overview
This project demonstrates Jenkins Remoting by configuring an SSH-based Jenkins agent on Debian running under WSL. The objective was to execute Jenkins build jobs on a dedicated agent instead of the built-in controller node.

## Architecture
- **Jenkins Controller:** Existing Jenkins instance running on port `8080`
- **Agent Name:** `linux-agent-1`
- **Agent Label:** `linux-agent`
- **Agent Linux User:** `jenkins-agent-2`
- **Remote Workspace:** `/home/jenkins-agent-2/workspace`
- **Connection Method:** SSH using ED25519 key authentication
- **Java Runtime:** OpenJDK 21

## Implementation
1. Verified the existing Jenkins controller and Java runtime.
2. Installed and enabled the OpenSSH server.
3. Created an ED25519 SSH key pair for agent authentication.
4. Configured the public key for the dedicated Linux agent account.
5. Added an SSH Username with private key credential in Jenkins.
6. Created and connected the permanent agent `linux-agent-1`.
7. Assigned the `linux-agent` label.
8. Created a Freestyle job named `remoting-agent-test`.
9. Restricted the job to the `linux-agent` label and executed a remote build.

## Verification
The `remoting-agent-test` job completed successfully.

Verified console output:
- Agent: `linux-agent-1`
- Execution user: `jenkins-agent-2`
- Workspace: `/home/jenkins-agent-2/workspace/remoting-agent-test`
- Java: OpenJDK 21
- Final build result: `SUCCESS`

## Security Considerations
- Used a dedicated Linux account for agent execution.
- Used SSH key-based authentication rather than password-based authentication.
- Stored the private key in Jenkins Credentials, not in the project repository.
- Never commit private keys, passwords, Jenkins secrets, or access tokens.
- For production environments, use verified SSH host keys and appropriately restricted permissions.

## Environment Limitations
The controller and agent run within the same Debian/WSL environment. The agent has a separate Jenkins node configuration and workspace, but this is not a separate physical machine.

## Skills Practiced
Jenkins, Jenkins Remoting, SSH, Linux user permissions, Java, Jenkins Credentials, agent labels, Freestyle jobs, and remote build verification.

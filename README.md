# Node.js Dockerized Application with Jenkins CI/CD

This repository contains a Node.js application Dockerized using Docker and integrated with Jenkins for continuous integration and deployment.

## Prerequisites

- Docker installed on your local machine
- Jenkins server set up and running

## Getting Started

To get started with this repository, follow the steps below:

1. Clone the repository to your local machine:

   ```bash
   git clone <repository-url>
   ```

2. Build the Docker image for the Node.js application:

   ```bash
   docker build -t node-app .
   ```

3. Run the Docker container:

   ```bash
   docker run -p 3000:3000 node-app
   ```

   The Node.js application will be accessible at `http://localhost:3000`.

## Jenkins Integration

This repository is integrated with Jenkins for automated building of the Node.js Docker container.

To set up Jenkins for building the Node.js container, follow these steps:

1. Configure a Jenkins job to build the Docker container:
   - Create a new Jenkins freestyle project.
   - In the **Source Code Management** section, specify the Git repository URL.
   - In the **Build** section, add a build step to execute the following shell commands:
     ```bash
     docker build -t node-app .
     ```
     
     ```bash
     docker rm -f node >/dev/null 2>&1 || true
     ```
     
     ```bash
     docker run -d -p 3000:3000 --name node node-app
     ```
   - Save the Jenkins job configuration.

2. Set up a webhook in the repository to trigger the Jenkins build:
   - In the repository settings, navigate to **Webhooks**.
   - Add a new webhook with the Jenkins job's URL as the payload URL.
   - Configure the webhook to trigger on push events.

Now, whenever changes are pushed to this repository, Jenkins will automatically build the Node.js Docker container.

## Contributing

If you'd like to contribute to this project, please follow these steps:

1. Fork the repository on GitHub.
2. Create a new branch with a descriptive name for your feature or bug fix.
3. Make the necessary changes in your branch.
4. Open a pull request to submit your changes.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- [Docker](https://www.docker.com/)
- [Jenkins](https://www.jenkins.io/)

Feel free to explore the code and customize it according to your requirements. Happy coding!

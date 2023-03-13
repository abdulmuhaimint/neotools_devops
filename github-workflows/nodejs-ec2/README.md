# Build and Deploy nodejs project to ec2  Github Action

This action builds and deploys your Node.js application to an Ubuntu server on a specific branch push. It runs on the ubuntu-latest environment and performs the following steps:

    Checkout source code
    Build the Node.js application using npm ci command
    Zip the build output to dist.tar.gz
    Deploy the build output to an EC2 instance
    Restart the Node.js application using PM2 process manager

## Usage
edit .yml file and change `[branchname]` to the target branch, eg: `branches: [dev]`  
Set the following secrets in github repository settings  
Contact devops team if you dont have access
```
VM_SSH_KEY : ssh private key of ec2 server
VM_HOST : ip address of ec2 server
TARGET_PATH : absolute path of the target folder where the project is located on the server
```
For project specific customization refer to the commented areas in the .yml file
The workflow will be triggered whenever a push event occurs on the specified branch. It will checkout the source code, build the application, create a compressed package, and then deploy it to your Ubuntu server using SSH. Finally, it will restart your Node.js application using PM2 process manager.

Note that you may need to adjust some of the script commands to fit your specific project requirements.

# https://www.youtube.com/watch?v=531i-n5FMRY&t=985s << this project is for n virginia region

#!/bin/bash

# Update the system
echo "Updating the system..."
sudo yum update -y

# Install Ruby and wget if not already installed
echo "Installing Ruby and wget..."
sudo yum install -y ruby
sudo yum install -y wget

# Download and install the CodeDeploy agent
echo "Downloading and installing the CodeDeploy agent..."
cd /home/ec2-user
wget https://aws-codedeploy-us-east-1.s3.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto

# Start the CodeDeploy agent
echo "Starting the CodeDeploy agent..."
sudo service codedeploy-agent start

# Check CodeDeploy agent status
echo "Checking CodeDeploy agent status..."
sudo service codedeploy-agent status

# Enable CodeDeploy agent on boot
echo "Enabling CodeDeploy agent on boot..."
sudo systemctl enable codedeploy-agent

echo "Installation and setup complete!"

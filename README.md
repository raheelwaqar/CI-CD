# CI-CD
 Sample code for running CodeBuild

 ## Troubleshooting

 ### Issue 1:
 I ran into issue while deploying the application using code build. Following is the issue that I faced:

 ```
 The overall deployment failed because too many individual instances failed deployment, too few healthy instances are available for deployment, or some instances in your deployment group are experiencing problems.
 ```
 #### Reason:
 
    Briefly what caused the problem:

    - Launch an instance WITHOUT any roles attached to it
    - Then install a codedeploy-agent on that machine
    - Only lastly attach an IAM role to the machine

#### Resolution:

First of all check the codedeploy agent logs by running the following command:
    
    cat /var/log/aws/codedeploy-agent/codedeploy-agent.log

You will see the permission denied issue in the logs. Restarting the CodeDeploy agent will resolve this issue. Run follwing command to resolve it:
    
    - sudo service codedeploy-agent stop
    - sudo service codedeploy-agent start

Check the status to make sure that CodeBuild agent is running now:
    
    sudo service codedeploy-agent status




    


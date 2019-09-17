# INSIGHTS DEV-OPS challenge solution
## instructions for running - 
docker-compose up -d db
docker-compose run --rm flaskapp //bin/bash -c "cd /opt/services/flaskapp/src && python -c  'import database; database.init_db()'"
docker-compose up -d

## Debugging process
After copying the github repo when we run the given commands because the secidn command is wrong, there needs to be an extra slash before bin.
After fixing that, there are furthermore changes required as the website is still not up and running. 
To start with the process of debugging first nginx should be up and running and we look at all the code needed for nginx to be configured, we look at the ports first and in the Docker-compose.yml file as it mentions all the requirements when we check the ports under the nginx ports the ports are written opposite as it should be 8080:80. 
After that we know that nginx is working but there is still some internal error. 
To solve that we look at the flask. Again the ports are not mentioned for the flask in docker-compose file, which is again fixed. 
But again there is error with the flask as it is not working.
So I tried running it on the local environment, and there are certain changes needed in the App.py file - 
in the app.route for the success function GET,POST method is mentioned to handle forms.
And again in app.run the port number is mention 5001 to make sure Flask runs well. 

And the final change needed - JSONify the output file to /success file to properly see changes on submitting entries.

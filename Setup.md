### Launching from a new server
Make sure you have [NodeJS](https://nodejs.org/) installed on your machine.
 - Get a fresh clone of the repository:
   ```
   git clone https://github.com/huytd/agar.io-clone
   ```
 - Navigate into the directory you just cloned the repository into:
   ```
   cd agar.io-clone
   ```
 - Install gulp globally (may require root privileges):
   ```
   npm install -g gulp
   ```
 - run apt-get install nodejs-legacy
 
 - Install the application dependencies:
   ```
   npm install
   ```
 - Run the server:
   ```
   gulp run
   ```

Your server should be listening to port 3000 by default.  You can change any of the default parameters by editing the `server/config.yml` file.

### Bluemix Installation
This assumes you've already signed up for a [IBM Bluemix](http://ibm.biz/bluemixsg) and [IBM Bluemix DevOps Services](https://hub.jazz.net) account.

Click the "Deploy to Bluemix button below.

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/huytd/agar.io-clone/agar-io-clone.git)

-or-

 1. Clone the project to your own github repository.
 2. Go to [IBM Bluemix DevOps Services](https://hub.jazz.net/) and [Create a Project](https://hub.jazz.net/create).
 3. Name your project and link to your cloned repository.
 4. Click on "Edit Code".
 5. Add a new file in your root directory called `manifest.yml` by clicking on File->New->File.
 6. Add this to your `manifest.yml` file. Change the name and host to something different. 

    ```
    ---
    applications:
    - name: agar-clone
      memory: 512M
      disk_quota: 1G
      buildpack: nodejs_buildpack
      host: agar-clone
      domain: mybluemix.net
      command: node server/server.js
      timeout: 180
      env:
        env_type: production
    ```
 7. Create a new launch configuration.
 8. Deploy your application and it will create a new instance on your [IBM Bluemix](http://ibm.biz/bluemixsg) account.

**OR**

1. Go to [agar-io-clone on IBM Bluemix DevOps Services](https://hub.jazz.net/project/justinlee/agar-io-clone).
2. Click on "Edit Code". This will clone a new repository to your account.
3. Follow steps 5-7 from above.

### Heroku Installation
**TODO**
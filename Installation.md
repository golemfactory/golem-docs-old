# Installing Golem

1. [Contact us](<mailto:testnet@golemproject.net>) to sign up for tests. You will be sent a link to the Golem package.

2. Install Docker

   Follow the official Docker installation guide for your operating system: [instruction](https://docs.docker.com/engine/installation/)
   
   After the installation remember to check if it's working properly by checking version and runnig a container example (you can find out how to this in the installation instruction). 

3. Download and extract Golem package.  

4. In terminal, go to the package directory and run application. The runner script may do some additional work on the first run. This process should take up to few minutes.

   - **On Windows**

      **Double-click the `golem.cmd` file.**

      If you want to pass additional parameters, open the windows command prompt and type (f.e.):

      `cd <path to the extracted packaged>`

      `golem -p 52.37.205.43:40102`

   - **On Linux**

     In terminal write: 

     `cd <path to the extracted packaged>`

     `sudo ./golem.sh --gui`

     _Optional: if you don't want to use `sudo` then create Docker group and add your user to this group. Follow the [instruction](https://docs.docker.com/engine/installation/linux/ubuntulinux/)._

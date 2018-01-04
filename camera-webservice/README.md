# camera-webservice

## Summary:
Here is a Python webservice called webservice.py written for this event.  Google won't help you with any information specifically about the script, but you will find lots of information about the libraries used in the script.  Proceed in steps.

### 1 - Setup the Raspberry Pi and take a photo
1. Install required prerequisites:
      0. **Step 0** - Get DNS services
          * edit /etc/resolve.conf and replace the exsisting DNS address to google DNS (8.8.8.8)
      1. **Step I** - Manual Installation using package managers:
          * Install `git` using package manager (hint: use `apt-get`)
      2. **Step II** - Automatic installation using Ansible configuration manager:
          * Install Ansible on your laptop or on your raspberry-pi (Hint: Raspbian OS is built on Debian Jessie)
          * Clone the git repo from github (hint: use `git` :) )
          * Update the `hosts` file with your Raspberry host name
          * Read through the Package_dependencies.yml file and try to understand what is the script doing
          * Execute the playbook Package_dependencies.yml. Make sure you use our `hosts` file (hint: -i)
2. Take a photo with `fswebcam` and transfer this to your laptop (`scp` can be your best friend), and verify the camera focus is good.  Repeat as necessary :-)

### 2 - Setup the camera-webservice
1. Copy the camera-webserivce `config.json.example` to `config.json`
2. Update all parameters to meet your needs
3. For the `camera_command` parameter these might be helpful:
    * Example linux USB camera: `fswebcam -r 1280x720 --jpeg 85 --no-banner -S 20`
    * Example native raspberry camera module: `raspistill -o`
    * Example windows usb camera: `CommandCam.exe /quiet /filename`

### 3 - Run the Camera webservice
1. Start it up with `python webservice.py`.  Do you see any errors? Troubleshoot and fix them.
1. Use your browser to load `http://ip_address:8080`  Does it report that everything is ok?  If not, troubleshoot and fix them.

### 4 -Take a photo
1. Use your browser to call the API:
 * `http://ip_address:8080/take_photo`
 *   Does it report that everything is ok?  Can you view your photo?  If not, troubleshoot and fix.
1. Use curl to call the API:
 * `curl http://ip_address:8080/take_photo`

# This is the project for the Carnyx Studios website


#### This repository contains:
- A Dockerfile which will be used to generate the image for the server.
- An nginx config file, one primed for localhost and one for deployment (in real nginx.conf directory)
- The code for the website.



## Website structure:
**index.html** must be the **main** file. nginx will read it as an equivilant to main.
All files for the website must be contained within the carnyx-site directory or subdirectories.


## For building and using the container:

<p>1. Build container image: <br>
<b> podman build -t carnyx-website . </b><br> 
<em>(the "." can be replaced with the location of the dockerfile to read from)</em>
</p>

<p>2. Run container image locally<br> 
<b>podman run -p 127.0.0.1:8080:80 -p 8443:8443 carnyx-website</b><br> 
<em>(-p 8443 directs external traffic to the containers ports, its tunneled port with cloudflared. -p 8080 allows for localhost testing)</em>
</p>

<p>3. Open container command line<br>
<b>podman exec -it <CONTAINER ID> sh </b><br>
<em>(this lets you interact with the container through cmd line as a standard linux OS</em>
</p>



## Useful command line tools:
<p>

> #### **curl http://localhost:8080** 
Returns the contents of the html of the webpage, but will return with curl (7) if the webpage is not up.<br>
You can replace the http address with whatever address you want to check.

> #### **podman ps** 
Will list all RUNNING containers. This is how you get their container IDs<br>
>> #### **podman ps -a** 
Will list ALL containers on disk.

> #### **podman stop -a** 
Stops all running containers<br>
*You can replace -a with a container id to stop that individual container*

> #### **podman rm -a** 
removes all container images. this means they will have to be rebuilt.<br>
*You can replace -a with a container id to delete that individual container*
</p>

## Packages installed with the Dockerfile:
- nano (for easy text editing in cmd line while in container)



## Useful Documentation:
- nginx: https://nginx.org/en/docs/
- podman: https://podman.io/docs

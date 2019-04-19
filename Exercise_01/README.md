# Exercise no.01 - Testing the client from the “oneclient" Docker container

In this exercise we learn how to 
* Use the Docker container with the already installed oneclient (see below `sudo docker run` command).
* Mount the current working directory ($PWD) in the Docker container (under `/mnt/src`).

## Requirements
* Access the EGI Training infrastructure (see section before).
* Generate the token to access the Onedata volume space (see section before).

## Configure the environment settings
Configure the environment variables before to launch the container. The following variables have to be exported in the Docker container:

<b>ONECLIENT_ACCESS_TOKEN</b>: Access token allowing to access all the spaces.</br>
<b>ONECLIENT_PROVIDER_HOST</b>: Name or IP of the Oneprovider the client should connect to.

<pre>
]$ export MOUNT_POINT=/mnt
]$ export ONECLIENT_ACCESS_TOKEN='Add here your access token'
]$ export ONECLIENT_PROVIDER_HOST=plg-cyfronet-01.datahub.egi.eu
</pre>

<b>IMPORTANT NOTICE: Please remember to run the Docker container in “privileged” mode to use the FUSE library.</b>

<pre>
]$ sudo docker run -it --privileged \
                   -e ONECLIENT_ACCESS_TOKEN=$ONECLIENT_ACCESS_TOKEN \
                   -e ONECLIENT_PROVIDER_HOST=$ONECLIENT_PROVIDER_HOST \
                   -e MOUNT_POINT=$MOUNT_POINT \
                   -v $PWD:/mnt/src --entrypoint bash onedata/oneclient:18.02.0-rc13    

Unable to find image 'onedata/oneclient:18.02.0-rc13' locally
18.02.0-rc11: Pulling from onedata/oneclient
3b37166ec614: Pull complete
[..]
Digest: sha256:893c78b10878fd41360477c1ffac1e45dbbedd3d18ef401213bb81c3d132b
Status: Downloaded newer image for onedata/oneclient:18.02.0-rc13
[..]
Connecting to provider 'plg-cyfronet-01.datahub.egi.eu:443' using session ID: '1993401975351113888'...
Getting configuration...
Oneclient has been successfully mounted in '/mnt/oneclient'.
</pre>

## Install missing libraries

<pre>
]$ apt-get update
]$ apt-get install -y vim wget python python-pip python-tk
]$ python -m pip install -U pip
]$ pip install ‘matplotlib==1.5.3’ requests
</pre>

## Mount the volume space 

<pre>
]$ oneclient -o allow_other -o nonempty --force-proxy-io --force-fullblock-read /mnt
</pre>

<b>IMPORTANT NOTICE: The Onedata volume space that will be used for this training session is: "EGI Foundation/CSV"</b>.


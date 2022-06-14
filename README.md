# Ubuntu 20.04 Docker Container with XFCE Desktop over VNC / noVNC

Did you ever wanted to start a fully-fledged Ubuntu Docker container with a full desktop experience?
If so, then this Docker image suits your needs: it provides quick access to an entire Ubuntu Desktop (XFCE) – directly from within the Docker container.
Therefore, it uses the tightvncserver to provide a VNC connection to the container and noVNC for simple VNC access with your browser.

IMPORTANT:
This image is for testing only.
Do not run it on any production systems or for any productive purposes.
Feel free to modify it as you like – build instructions are given below.

## Build & Install

- **Clone** this repository: `git clone https://github.com/iphoneintosh/ubuntu-docker && cd ubuntu-docker`
- **Build** the Docker image: `docker build -t ubuntu-docker .`
  - Optional: `--build-arg VNCPWD=changeme` - set a password for the VNC access (default: `changeme`)
  - Optional: `--build-arg VNCDISPLAY=1920x1080` - set a display resolution for the VNC server (default: `1920x1080`)
  - Optional: `--build-arg VNCDEPTH=16` - set a display depth for the VNC server (default: `16`)
- **Run** the container: `docker run -it -p <INSERT_FREE_HOST_PORT>:9090 --name ubuntu-container ubuntu-docker`
  - Choose a free port on your host system and replace it in `<INSERT_FREE_HOST_PORT>`
- Open `https://localhost:<INSERT_FREE_HOST_PORT>/vnc.html` in your browser to interact with the Ubuntu XFCE desktop
  - If a certificate warning is shown, verify the SHA256 certificate fingerprint with the fingerprint shown on the command prompt on which you just started the container
  - If prompted for a password, enter the default password `changeme` or the password you set while building the image

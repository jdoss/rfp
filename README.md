# RFP: rtorrent, flood, and plex

RFP is a quick and dirty media stack built on Docker. It comes with [rtorrent](https://github.com/rakshasa/rtorrent) for downloading torrents, [flood](https://github.com/jfurrow/flood) for a pretty frontend for rtorrent, and [plex](https://www.plex.tv/) to help manage all those public domain movies that you are going to download.

## Quick Start

Build local docker images:

```
docker build -t rfp-flood -f Dockerfile.flood .
docker build -t rfp-rtorrent -f Dockerfile.rtorrent .
docker build -t rfp-plex -f Dockerfile.plex .
```

Start RFP:

` docker-compose up -d`

### Finish Setup

https://localhost:32400


### Remote Server

1. Open a Terminal window or your command prompt
2. Enter the following command
3. `ssh 192.168.1.55 -L 8888:localhost:32400`
4. Goto http://localhost:8888/web and enable remote access to finish the setup.

### Ports

Forward these ports from your router to `49264`, `6881` for torrents and `32400` for Plex if you want to allow outside access to your media. Run the command below if you are are running these containers on a distro that uses firewalld. Good luck, have fun.

`sudo firewall-cmd --zone=FedoraServer --add-port=32400/tcp --add-port=3005/tcp --add-port=8324/tcp --add-port=32469/tcp --add-port=1900/udp --add-port=32410/udp --add-port=32412/udp --add-port=32413/udp --add-port=32414/udp --add-port=6881/tcp --add-port=6881/udp --add-port=49264/tcp --add-port=49264/udp`


## Todo

* Give these processes some sort of proper init.
* Figure out how to to pass a Plex claim token at the initial startup to skip SSH tunnel step.

## License

The MIT License

Copyright (c) 2017 Joe Doss

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

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

Forward these ports from your router to `49164`, `6881` for torrents and `32400` for Plex if you want to allow outside access to your media. Good luck, have fun.

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

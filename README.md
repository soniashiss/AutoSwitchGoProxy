
# AutoSwitchGoProxy

Based on GOPROXY

Change:

    Auto switch:

        when the request is private repository, it won't use proxy
        when the request is not private repository, it will use athens proxy by default

FAQ：

1. username and password for the private repository?

    see https://golang.org/doc/faq#git_https

2. enviroment needed?

    * golang version > 1.11
    * GOPROXY is not set
    * it should have access to both internal network(to get private repository) and internet


# GOPROXY [![CircleCI](https://circleci.com/gh/goproxyio/goproxy.svg?style=svg)](https://circleci.com/gh/goproxyio/goproxy)

A global proxy for go modules. see: [https://goproxy.io](https://goproxy.io)

## Build
    go generate
    go build

## Started
    
    ./goproxy -listen=0.0.0.0:80 -cacheDir=./cacheDir -internalproxy=your_private_repository

## Use docker image

    docker run -d -p80:8081 goproxy/goproxy

Use the -v flag to persisting the proxy module data (change ___cacheDir___ to your own dir):

    docker run -d -p80:8081 -v cacheDir:/go goproxy/goproxy

## Docker Compose

    docker-compose up

## Appendix

1. set `export GOPROXY=http://localhost` to enable your goproxy.
2. set `export GOPROXY=` to disable it.

# Arquillian Phantom Binary

This project contains a binary of [PhantomJS](http://phantomjs.org/) for distribution as Maven artifact suitable for each supported OS family and architecture.

The distribution in a Maven repository allows to run PhantomJS projects without a need to have the PhantomJS executable installed locally. It also helps to manage dependency on particular PhantomJS version.

## Installing

The general schema for installing the project for the wanted OS is:

    mvn clean install -P<windows|macosx|linux-32|linux-64>
    
    
To install binaries for all platforms:
    
    mvn clean install -Pwindows
    mvn clean install -Pmacosx
    mvn clean install -Plinux-32
    mvn clean install -Plinux-64

## Deploying

First, verify the right versions in `pom.xml`.

Make sure to point to valid `release-settings.xml`.

Deploy to staging area:

    mvn -s ../../release-settings.xml clean deploy -Pwindows
    mvn -s ../../release-settings.xml clean deploy -Pmacosx
    mvn -s ../../release-settings.xml clean deploy -Plinux-32
    mvn -s ../../release-settings.xml clean deploy -Plinux-64
    mvn -s ../../release-settings.xml clean deploy

Close staging repository and verify release.

Release repository.

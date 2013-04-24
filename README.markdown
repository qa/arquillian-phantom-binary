# Arquillian Phantom Binary

This project contains a binary of [PhantomJS](http://phantomjs.org/) for distribution as Maven artifact suitable for each supported OS family and architecture.

The distribution in a Maven repository allows to run PhantomJS projects without a need to have the PhantomJS executable installed locally. It also helps to manage dependency on particular PhantomJS version.

## Installing

The general schema for installing the project for the wanted OS is:

    mvn clean install -P<windows|macosx|linux-32|linux-64>
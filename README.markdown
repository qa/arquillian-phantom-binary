# Arquillian Phantom Binary

This project contains a binary of [PhantomJS](http://phantomjs.org/) for distribution as Maven artifact suitable for each supported OS family and architecture.

The distribution in a Maven repository allows to run PhantomJS projects without a need to have the PhantomJS executable installed locally. It also helps to manage dependency on particular PhantomJS version.

## Usage


Add following snippet to your project's POM:

    <properties>
        <version.phantomjs>1.9.0</version.phantomjs>
    </properties>

    <profiles>
        <profile>
            <id>linux</id>
            <activation>
                <os>
                    <family>unix</family>
                </os>
            </activation>
            <dependencies>
                <dependency>
                    <groupId>org.jboss.arquillian.extension</groupId>
                    <artifactId>arquillian-phantom-binary</artifactId>
                    <version>${version.phantomjs}</version>
                    <classifier>unix_${os.arch}</classifier>
                </dependency>
            </dependencies>
        </profile>
        <profile>
            <id>mac</id>
            <activation>
                <os>
                    <family>mac</family>
                </os>
            </activation>
            <dependencies>
                <dependency>
                    <groupId>org.jboss.arquillian.extension</groupId>
                    <artifactId>arquillian-phantom-binary</artifactId>
                    <version>${version.phantomjs}</version>
                    <classifier>mac</classifier>
                </dependency>
            </dependencies>
        </profile>
        <profile>
            <id>windows</id>
            <activation>
                <os>
                    <family>windows</family>
                </os>
            </activation>
            <dependencies>
                <dependency>
                    <groupId>org.jboss.arquillian.extension</groupId>
                    <artifactId>arquillian-phantom-binary</artifactId>
                    <version>${version.phantomjs}</version>
                    <classifier>windows</classifier>
                </dependency>
            </dependencies>
        </profile>
    </profiles>

## Installing

The general schema for installing the project for the wanted OS is:

    mvn clean install -P<windows|linux|mac> -Dtarget.os.arch=<...> -Dlinux.arch=<i686|x86_64>

### Linux

There is a different binary for 64 architecture:

    mvn clean install -Plinux -Dtarget.os.arch=amd64 -Dlinux.arch=x86_64

and 32bit one:

    mvn clean install -Plinux -Dtarget.os.arch=x86 -Dlinux.arch=i686

### Windows

    mvn clean install -Pwindows

### Mac OS X

    mvn clean install -Pmac

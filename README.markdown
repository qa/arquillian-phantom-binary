# Binary for PhantomJS

This project contains a binary of [PhantomJS](http://phantomjs.org/) suitable for the given OS family and architecture.

## Usage


Add following snippet to your project's POM:

    <properties>
        <version.phantomjs>1.8.0</version.phantomjs>
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
                    <groupId>org.jboss.phantomjs</groupId>
                    <artifactId>phantomjs-binary</artifactId>
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
                    <groupId>org.jboss.phantomjs</groupId>
                    <artifactId>phantomjs-binary</artifactId>
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
                    <groupId>org.jboss.phantomjs</groupId>
                    <artifactId>phantomjs-binary</artifactId>
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
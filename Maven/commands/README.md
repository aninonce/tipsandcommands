# Maven commands

<a id="toc"></a>
## Table of contents

1. [Contribution guidelines](#contri_guidelines)
1. [Executing maven commands via command line](#exec_cmd)
    1. [How to execute](#how_to)
1. [Maven help](#help)
1. [Check maven version](#check_version)
1. [Lifecycle, phases and goals ](#lifecycle_phases_goals)
1. [Path, settings and local repo](#path_settings_repo)
1. [Help describe ](#help_describe)
1. [Clean project](#clean)
1. [Install](#install)
1. [Skipping test](#skipping_test)

<a id="contri_guidelines"></a>
## Contribution guidelines [^](#toc)

1. Fork -> Clone the project.
2. Make change.
3. Raise pull request & merge.

<a id="exec_cmd"></a>
## Executing maven commands via command line [^](#toc)
Commands below assume that maven is installed / available + accessible on target system.
Go to the root of the project / folder where pom.xml (pom: project object model) exist to execute commands.

Though commands below are tested on maven verison: 3.X
these are expected to run on most of the maven versions.
If a command is not longer in use / is changed, make change and raise pull request.

<a id="how_to"></a>
### How to execute [^](#toc)
Options are allowed before and after task names.
```text
mvn [taskName...]  [optionName...]
mvn clean build -X  // e.g.
```

<a id="help"></a>
## Maven help [^](#toc)

```text
mvn -h
mvn --help
```

<details>
    <summary>Sample output: </summary>

```text
usage: mvn [options] [<goal(s)>] [<phase(s)>]

Options:
 -am,--also-make                        If project list is specified, also
                                        build projects required by the
                                        list
 -amd,--also-make-dependents            If project list is specified, also
                                        build projects that depend on
                                        projects on the list
 -B,--batch-mode                        Run in non-interactive (batch)
                                        mode (disables output color)
 -b,--builder <arg>                     The id of the build strategy to
                                        use
 -C,--strict-checksums                  Fail the build if checksums don't
                                        match
 -c,--lax-checksums                     Warn if checksums don't match
 -cpu,--check-plugin-updates            Ineffective, only kept for
                                        backward compatibility
 -D,--define <arg>                      Define a system property
 -e,--errors                            Produce execution error messages
 -emp,--encrypt-master-password <arg>   Encrypt master security password
 -ep,--encrypt-password <arg>           Encrypt server password
 -f,--file <arg>                        Force the use of an alternate POM
                                        file (or directory with pom.xml)
 -fae,--fail-at-end                     Only fail the build afterwards;
                                        allow all non-impacted builds to
                                        continue
 -ff,--fail-fast                        Stop at first failure in
                                        reactorized builds
 -fn,--fail-never                       NEVER fail the build, regardless
                                        of project result
 -gs,--global-settings <arg>            Alternate path for the global
                                        settings file
 -gt,--global-toolchains <arg>          Alternate path for the global
                                        toolchains file
 -h,--help                              Display help information
 -l,--log-file <arg>                    Log file where all build output
                                        will go (disables output color)
 -llr,--legacy-local-repository         Use Maven 2 Legacy Local
```
</details>

<a id="check_version"> </a>
## Check maven version [^](#toc)

```text
mvn -v
mvn --version
```

<details>
  <summary>Sample output: </summary>

```text
Apache Maven 3.6.2 (40f52333136460af0dc0d7232c0dc0bcf0d9e117; 2019-08-27T11:06:16-04:00)
Maven home: /mnt/c/install/apache-maven-3.6.2
Java version: 11.0.8, vendor: Azul Systems, Inc., runtime: /usr/lib/jvm/zulu-11-amd64
Default locale: en, platform encoding: UTF-8
OS name: "linux", version: "5.10.60.1-microsoft-standard-wsl2", arch: "amd64", family: "unix"
```
</details>

<a id="lifecycle_phases_goals"> </a>
## Lifecycle, phases and goals [^](#toc)
Maven has concept of lifecycle, phases (a lifecycle is divided in different phases) & goals. 
```text
Built-in lifecycles: 
default:    Handles your project deployment
clean:      Handles project cleaning
site:       Handles the creation of project's web site
```
Most of the time default and clean life cycles are used.
To learn more about different phases of above life cycle, check [here](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference).


<a id="path_settings_repo"> </a>
## Path, settings and local repo [^](#toc)
If maven is installed, most possibly maven path (the location where maven is installed) can be accessed by
```text
echo %MAVEN_HOME%  // for windows
echo $MAVEN_HOME  // for unix, mac
mvn --version  // if the maven_home is blank, use this command to check maven installed location
```
If the result of above command is blank, or not intended it can be changed to where the maven is installed on the system.

Usually local maven repo (where all libraries / dependencies are downloaded and stored locally) path is : 

```text
windows: C:\Users\<userName>\.m2
linux: /home/<userName>/.m2
mac: /Users/<userName>/.m2
```

However in case the above directory does not exist / dependencies are not found above even after running any maven command, check settings.xml in MAVEN_HOME/conf/ directory and check the value under:

```text
<settings>
    <localRepository><path to maven local repo></localRepository>
```

Maven can also be instructed to use a local repo without changing settings.xml

```text
mvn -Dmaven.repo.local=/my/local/repository/path clean install  // e.g.
```
<a id="help_describe"> </a>
## Help describe [^](#toc)
It is a plugin which display information, list of the attributes for a plugin / goal.
Information and usage can be found [here](https://maven.apache.org/plugins/maven-help-plugin/describe-mojo.html).
This is equivalent of Gradle help command. E.g. 'gradle help [commandName]'.
-Ddetail=true option is used to show more information. Result is usually more useful with this option.
```text
mvn help:describe -Dcmd=clean // to get more info use -Ddetail=true flag e.g. mvn help:describe -Dcmd=clean -Ddetail=true
mvn help:describe -Dcmd=compile  // to get more info use -Ddetail=true flag e.g. mvn help:describe -Dcmd=compile -Ddetail=true
mvn help:describe -Dplugin=com.mycila:license-maven-plugin // description about plugin
mvn help:describe -Dplugin=com.mycila:license-maven-plugin:4.0 // description about specific version of plugin
mvn help:describe -Dplugin=com.mycila:license-maven-plugin:4.0 -Dgoal=check -Ddetail=true  // description about specific goal of a plugin
mvn help:describe -DgroupId=org.somewhere -DartifactId=some-plugin -Dversion=0.0.0
```

<details>
  <summary>Sample output: mvn help:describe -Dcmd=clean </summary>

```text
[INFO] --- maven-help-plugin:3.1.0:describe (default-cli) @ pinot ---
[INFO] 'clean' is a phase within the 'clean' lifecycle, which has the following phases:
* pre-clean: Not defined
* clean: org.apache.maven.plugins:maven-clean-plugin:2.5:clean
* post-clean: Not defined
```
</details>

<details>
  <summary>Sample output: mvn help:describe -Dcmd=compile </summary>

```text
[INFO] --- maven-help-plugin:3.1.0:describe (default-cli) @ pinot ---
[INFO] 'compile' is a phase corresponding to this plugin:

It is a part of the lifecycle for the POM packaging 'pom'. This lifecycle includes the following phases:
* validate: Not defined
* initialize: Not defined
* generate-sources: Not defined
* process-sources: Not defined
* generate-resources: Not defined
* process-resources: Not defined
* compile: Not defined
* process-classes: Not defined
* generate-test-sources: Not defined
* process-test-sources: Not defined
* generate-test-resources: Not defined
* process-test-resources: Not defined
* test-compile: Not defined
* process-test-classes: Not defined
* test: Not defined
* prepare-package: Not defined
* package: Not defined
* pre-integration-test: Not defined
* integration-test: Not defined
* post-integration-test: Not defined
* verify: Not defined
* install: org.apache.maven.plugins:maven-install-plugin:2.4:install
* deploy: org.apache.maven.plugins:maven-deploy-plugin:2.7:deploy
```
</details>

<details>
  <summary>Sample output: mvn help:describe -Dplugin=com.mycila:license-maven-plugin / mvn help:describe -Dplugin=com.mycila:license-maven-plugin:4.0 </summary>

```text
[INFO] --- maven-help-plugin:3.1.0:describe (default-cli) @ pinot ---
[INFO] com.mycila:license-maven-plugin:4.0

Name: license-maven-plugin
Description: Maven 2 plugin to check and update license headers in source
  files
Group Id: com.mycila
Artifact Id: license-maven-plugin
Version: 4.0
Goal Prefix: license

This plugin has 4 goals:

license:check
  Description: Check if the source files of the project have a valid license
    header

license:format
  Description: Reformat files with a missing header to add it

license:help
  Description: Display help information on license-maven-plugin.
    Call mvn license:help -Ddetail=true -Dgoal=<goal-name> to display parameter
    details.

license:remove
  Description: Remove the specified header from source files

For more information, run 'mvn help:describe [...] -Ddetail'
```
</details>

<details>
  <summary>Sample output: mvn help:describe -Dplugin=com.mycila:license-maven-plugin:4.0 -Dgoal=check -Ddetail=true </summary>

```text
[INFO] --- maven-help-plugin:3.1.0:describe (default-cli) @ pinot ---
[INFO] Mojo: 'license:check'
license:check
  Description: Check if the source files of the project have a valid license
    header
  Implementation: com.mycila.maven.plugin.license.LicenseCheckMojo
  Language: java
  Bound to phase: verify

  Available parameters:

    aggregate (Default: false)
      User property: license.aggregate
      You can set this flag to true if you want to check the headers for all
      modules of your project. Only used for multi-modules projects, to check
      for example the header licenses from the parent module for all sub
      modules.

    concurrencyFactor (Default: 1.5)
      User property: license.concurrencyFactor
      Maven license plugin uses concurrency to check license headers. This
      factor is used to control the number of threads used to check. The rule
      is:
      <nThreads> = <number of cores> * concurrencyFactor
      The default is 1.5.

    defaultBasedir (Default: ${basedir})
      Alias: basedir
      Required: true
      User property: license.basedir
      The base directory, in which to search for project files. This is named
      `defaultBaseDirectory` as it will be used as the default value for the
      base directory. This default value can be overridden in each LicenseSet
.
.
.
```
</details>

<a id="clean"> </a>
## Clean project [^](#toc)
Clean the target directory where project is build.
```text
mvn clean
```

<details>
  <summary>Sample output: </summary>

```text
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Detecting the operating system and CPU architecture
[INFO] ------------------------------------------------------------------------
[INFO] os.detected.name: linux
[INFO] os.detected.arch: x86_64
[INFO] os.detected.version: 5.10
[INFO] os.detected.version.major: 5
[INFO] os.detected.version.minor: 10
[INFO] os.detected.release: ubuntu
[INFO] os.detected.release.version: 20.04
[INFO] os.detected.release.like.ubuntu: true
[INFO] os.detected.release.like.debian: true
[INFO] os.detected.classifier: linux-x86_64
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] Pinot                                                              [pom]
[INFO] Pinot Service Provider Interface                                   [jar]
[INFO] Pinot Segment Service Provider Interface                           [jar]
[INFO] Pinot Plugins                                                      [pom]
[INFO] Pinot Metrics                                                      [pom]
[INFO] Pinot Yammer Metrics                                               [jar]
.
.
.
[INFO] -----------------------< org.apache.pinot:pinot >-----------------------
[INFO] Building Pinot 0.10.0-SNAPSHOT                                    [1/63]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ pinot ---
[INFO] Deleting /mnt/c/Users/Ankit Singh/git/ankit_repo/pinot/target
[INFO]
[INFO] ---------------------< org.apache.pinot:pinot-spi >---------------------
[INFO] Building Pinot Service Provider Interface 0.10.0-SNAPSHOT         [2/63]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ pinot-spi ---
[INFO]
[INFO] -----------------< org.apache.pinot:pinot-segment-spi >-----------------
[INFO] Building Pinot Segment Service Provider Interface 0.10.0-SNAPSHOT [3/63]
.
.
.
[INFO] Pinot .............................................. SUCCESS [  0.273 s]
[INFO] Pinot Service Provider Interface ................... SUCCESS [  0.017 s]
[INFO] Pinot Segment Service Provider Interface ........... SUCCESS [  0.012 s]
[INFO] Pinot Plugins ...................................... SUCCESS [  0.010 s]
.
.
.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.585 s
[INFO] Finished at: 2022-01-04T11:29:46-05:00
[INFO] ------------------------------------------------------------------------
```
</details>

<a id="install"> </a>
## Install [^](#toc)
Build the project and install the artificat in local maven repo.
```text
mvn install
mvn clean install  // first run the clean and then install. Useful in case compilation any other phases which install runs could not be executed due to previous version of the files
```
<details>
    <summary>Sample output: </summary>

```text
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Detecting the operating system and CPU architecture
[INFO] ------------------------------------------------------------------------
[INFO] os.detected.name: linux
[INFO] os.detected.arch: x86_64
[INFO] os.detected.version: 5.10
[INFO] os.detected.version.major: 5
[INFO] os.detected.version.minor: 10
[INFO] os.detected.release: ubuntu
[INFO] os.detected.release.version: 20.04
[INFO] os.detected.release.like.ubuntu: true
[INFO] os.detected.release.like.debian: true
[INFO] os.detected.classifier: linux-x86_64
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO]
[INFO] Pinot                                                              [pom]
[INFO] Pinot Service Provider Interface                                   [jar]
[INFO] Pinot Segment Service Provider Interface                           [jar]
[INFO] Pinot Plugins                                                      [pom]
[INFO] Pinot Metrics                                                      [pom]
.
.
.
[INFO] -----------------------< org.apache.pinot:pinot >-----------------------
[INFO] Building Pinot 0.10.0-SNAPSHOT                                    [1/63]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO]
[INFO] --- maven-checkstyle-plugin:3.1.2:check (checkstyle) @ pinot ---
[INFO]
```

</details>

<a id="skipping_test"> </a>
## Skipping test [^](#toc)
```text
via command line:
    mvn -DskipTests <commands...>  // skips running test phase, however test classes will be compiled
    mvn -Dmaven.test.skip=true  <commands...>  // skips compiling and running test phase
Tests can also be excluded via configuration:
    With following change in pom.xml

    skip all tests:
        <properties>
            <maven.test.skip>true</maven.test.skip>
        </properties>

    skip specific folder from test:
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <configuration>
                <excludes>
                    <exclude>SampleTest.java</exclude>
                </excludes>
            </configuration>
        </plugin>
```
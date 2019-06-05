Bamboo Mutex Plugin
===================

This is an [Atlassian Bamboo](http://www.atlassian.com/software/bamboo) plugin that allows you to make two or more plans "mutually exclusive". That means that those plans will never be run at the same time, even if agents are available to run them. This is useful if you have shared resources that can only be accessed by one plan at a time.


Installation
------------

Use the [Bamboo plugin manager](https://confluence.atlassian.com/display/BAMBOO/Add-ons) to install the latest version of this plugin's jar which is checked-in binary under target/ for your convenience.

You may have to restart Bamboo after installing the plugin.


Usage
-----

The plugin is configured on the "Miscellaneous" tab of the plan configuration. There is a single text entry field that allows you to specify the mutex "key" for the plan. If two or more plans have the same mutex key (case sensitive), this plugin will prevent them from running simultaneously.

Note that specifying multiple keys on a single plan is not supported right now (could be done as an enhancement if there is demand). Use a single key with only letters and numbers (no dashes) to be on the safe side.


Building From Source
--------------------

This is built using the standard Atlassian SDK. Full instructions on how to set up and use the SDK are available in the [Atlassian plugin SDK documentation](https://developer.atlassian.com/display/DOCS/Introduction+to+the+Atlassian+Plugin+SDK). The old 4.1.2 version of the SDK has been tested upto Bamboo 6.7.2; newer versions of the SDK may fail to build. In short, from the root of this plugin on a Linux host:

1. Make sure Java is installed and JAVA_HOME is set.
   * For example, `sudo apt-get install maven` will install the necessary dependencies on Ubuntu.
2. Download the old [Atlassian Plugin SDK 4.1.2](https://marketplace.atlassian.com/apps/1210993/atlassian-plugin-sdk-tgz/version-history) as tgz.
3. `tar xfz ~/Downloads/atlassian-plugin-sdk-4.1.2.tar.gz`
4. `chmod a+rx atlassian-plugin-sdk-4.1.2/apache-maven/bin/*`
5. Chdir to the root of this plugin, and execute
   * `atlassian-plugin-sdk-4.1.2/apache-maven/bin/mvn clean install`
   * Type something for the GPG key (not relevant)
6. Logon to bamboo, addons, and upload the JAR from `target/bamboo-mutex-plugin-1.1-SNAPSHOT.jar`

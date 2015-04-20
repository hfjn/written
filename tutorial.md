# Setting up the ACSE Development Environment on OS X

Install brew
`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

Install cask
`brew install caskroom/cask/brew-cask`

Install java
`brew cask install java`

Install wildfly
`brew install wildfly`

open .bash_profile with:
`vi .bash_profile`

and add:

`export JBOSS_HOME=/usr/local/opt/wildfly-as/libexec
export PATH=${PATH}:${JBOSS_HOME}/bin`

Add a user with:
`add-user.sh`

Start wildfly with:
`standalone.sh`

access it at 127.0.0.1:9990

> Go to Manage Deployments and click Add Content to upload hsqldb.jar. Make sure that the deployed file is enabled.

> Go to Configuration > Connector > Datasources and click Add. Use the following information to create a datasource:
Name: DefaultDS
JNDI Name: java:/DefaultDS
Choose hsqldb.jar as driver
Connection URL: jdbc:hsqldb:${jboss.server.data.dir}${/}hypersonic${/}localDB;shutdown=true
username: sa

after applying datasource restart the server

>Enable the new datasource.
In order to stop the server, press CTRL-C in the console window that was opened during step 3.

install eclipse-modeling
`brew cask install eclipse-modeling`

after this the original [tutorial](http://wwu-pi.github.io/tutorials/lectures/acse/010_setting_up_the_dev_environment.html) can be followed again.

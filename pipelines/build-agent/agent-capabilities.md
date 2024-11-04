# Capabilities - Agent UI
maven mvn
java java

# Maven
Install maven on the agent
`apt update && apt install -y maven`
Add capability on the agent using Agent UI
# JDK Software
## request-logger
```apt update && apt install -y openjdk-11-jdk
export JAVA_HOME_11_X64="/usr/lib/jvm/java-11-openjdk-amd64"

echo "export JAVA_HOME_11_X64=$JAVA_HOME_11_X64" >> /etc/profile
echo "export PATH=$JAVA_HOME_11_X64/bin:$PATH" >> /etc/profile```
## spring-petclinic
```apt update && apt install -y openjdk-17-jdk
export JAVA_HOME_17_X64="/usr/lib/jvm/java-17-openjdk-amd64"

echo "export JAVA_HOME_17_X64=$JAVA_HOME_17_X64" >> /etc/profile
echo "export PATH=$JAVA_HOME_17_X64/bin:$PATH" >> /etc/profile```
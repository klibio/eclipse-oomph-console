# eval.md

```bash
export PATH=$PATH:/Users/peterkir/Downloads/_tbd_/apache-maven-3.9.6/bin
export PATH=/Library/Java/JavaVirtualMachines/temurin-17.jdk/Contents/Home/bin:$PATH

java --version

export JAVA_TOOL_OPTIONS="-Dfile.encoding=UTF-8 -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true -Dtycho.disableP2Mirrors=true"
export MAVEN_OPTS="-Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true -Dtycho.disableP2Mirrors=true"
```


```bash
# test
mvn clean verify -Possrh -DskipTests -o

mvn org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=1.0.5 -o


mvn clean deploy -Possrh,oomph-p2 -DskipTests
mvn org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=1.0.6.qualifier -o

# to be evaluated
mvn org.eclipse.tycho.extras:tycho-version-bump-plugin:update-product -DnewVersion=1.0.5 -o
mvn org.eclipse.tycho.extras:tycho-version-bump-plugin:update-target -DnewVersion=1.0.5 -o
```

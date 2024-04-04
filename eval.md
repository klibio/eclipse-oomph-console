# eval.md



## versioning and releasing

```bash
# verify build before release
./mvnw clean verify -Possrh -DskipTests -o

# configure version for release (MANIFEST and pom) - see https://stackoverflow.com/a/34119136/2918516
./mvnw org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=1.0.7 -o

# releae to sonatype
./mvnw clean deploy -Possrh -DskipTests

# increase version to new snapshot
./mvnw org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=1.0.8.qualifier -o
```

##

```bash
./mvnw clean install -DskipTests
./mvnw -pl org.eclipse.oomph.console.tp,org.eclipse.oomph.console.core,org.eclipse.oomph.console -am clean package -DskipTests -o
./mvnw -pl org.eclipse.oomph.console.product -am clean package -DskipTests -o
```

## miscellaneous

```bash
export PATH=$PATH:/Users/peterkir/Downloads/_tbd_/apache-maven-3.9.6/bin
export PATH=/Library/Java/JavaVirtualMachines/temurin-17.jdk/Contents/Home/bin:$PATH
java --version
export JAVA_TOOL_OPTIONS="-Dfile.encoding=UTF-8 -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true -Dtycho.disableP2Mirrors=true"
export MAVEN_OPTS="-Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true -Dtycho.disableP2Mirrors=true"
```

```bash
# to be evaluated - see tycho-version-bump-plugin in `pom.xml`
mvn org.eclipse.tycho.extras:tycho-version-bump-plugin:update-product -DnewVersion=1.0.5 -o
mvn org.eclipse.tycho.extras:tycho-version-bump-plugin:update-target -DnewVersion=1.0.5 -o
```

## Javadoc

* https://stackoverflow.com/questions/59071851/how-to-force-a-javadoc-jar-even-though-there-is-no-public-javadoc
# eval.md

## versioning and deployment to sonatype maven snapshot and release repo

### deploy to SNAPSHOT repository
```bash
# verify build before deployment (snapshot or release)
./mvnw clean verify -Possrh -DskipTests -o
# deploy to sonatype SNAPSHOT repo (happes implicitly becuase qualifier/SNAPSHOTS are attached in versions)
./mvnw clean deploy -Possrh -DskipTests
```

### deploy to RELEASE repository
```bash
# verify build before deployment (snapshot or release)
./mvnw clean verify -Possrh -DskipTests -o
# configure version for RELEASE (MANIFEST and pom) - see https://stackoverflow.com/a/34119136/2918516
./mvnw org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=1.0.9 -o
# deploy to sonatype RELEASE repo
./mvnw clean deploy -Possrh -DskipTests

# start new dev cycle - increase version to new qualifier/SNAPSHOTS
./mvnw org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=1.0.10.qualifier -o
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
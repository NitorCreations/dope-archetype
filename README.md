# Developer Oriented Presentation Engine Archetype #

Maven archetype for creating DOPE slidesets.

## Using ##

 * Generate maven project

```
mvn archetype:generate -DarchetypeVersion=1.8 -DarchetypeArtifactId=dope-archetype \
  -DarchetypeGroupId=com.nitorcreations -DgroupId=foo.bar \
  -DartifactId=baz-prez -DinteractiveMode=false
```

 * Build project

```
cd baz-prez; mvn clean install
```

 * Run presentation with http server on port 9999, with wiimote, with spinning slide transitions (default is bump-and-fade)

```
java -Dwiimote=true -Dhttpport=9999 -Dcontroller=foo.bar.SpinController -jar target/jfx/app/baz-prez-1.0-SNAPSHOT-jfx.jar
```

 * Presentation as a zip in

```
target/baz-prez-1.0-SNAPSHOT.zip
```

## Optional Parameters ##

 * ```developerName``` Used on the title slide and put into the developers section in the presentation pom.
 * ```organizationName``` Used on the title slide and put into the organization section in the pom.
 * ```inceptionYear``` Used as copyright year on the title slide and put into the inceptionYear section in the pom.
 * ```name``` Used in the title of all slide html sources and on the title slide. If not given, artifactId with dashes replaced with spaces and words capitalized is used.
 * ```theme``` Used for the name of css files from the pom configuration of the ```dope-maven-plugin``` in the pom.
    * Archetype currently has themes 'dark' and 'light'. 'dark' is the default 

### Example with all optional parameters defined ###

```
mvn archetype:generate -DarchetypeVersion=1.8 -DarchetypeArtifactId=dope-archetype \
  -DarchetypeGroupId=com.nitorcreations -DgroupId=foo.bar \
  -DdeveloperName="Pasi Niemi" -DorganizationName="Nitor Creations" \
  -DinceptionYear=2013 -Dname="Baz Bar Awesomeness" \
  -Dtheme=light -DartifactId=baz-prez -DinteractiveMode=false
```

## Custom transitions ##

All of the code that runs the transtions is included in the created project. Just extend ```${package}.BaseController``` to make your own.

# word-count-beam

> Project built following the Beam Quickstart for Java.

## Process

This Apache Beam big data project was created by:

1. Following Google Colabs [Beam Quickstart for Java](https://beam.apache.org/get-started/quickstart-java/)
2. Adding README.md and .gitignore files
3. Git init/add/commit/push to repo. Create GitHub repo word-count-beam (same name as folder) with no README.md or .gitignore. 

   ```Bash
   git init
   git remote add origin https://github.com/denisecase/word-count-beam.git
   git branch -M main
   git add .
   ```

-----

## Recommended Tools (on Windows)

- Git
- PowerShell (cross-platform terminal)
- Chocolatey (package manager for Windows)
- [Open JDK 17](https://adoptium.net/) (17 seems to work fine)
- Maven (build tool for JVM projects)
- VS Code (code editor)
- Optional: Winget (package manager for Windows)

-----

## Installation

- Recommended: Use Chocolatey to install all
- JDK Options 
- Java Warning - exactly one path
- Verify installations

### Recommended - Chocolatey for All

```PowerShell
choco install git -y
choco install openjdk -y
choco install maven -y
choco install vscode -y
choco upgrade all -y
refreshenv
```

### JDK Installation Alternatives

- Install Open JDK from Adoptium
- Or use winget to install Microsoft Open JDK 17

```PowerShell
winget install Microsoft.OpenJDK.17
```

### :star Warning: Exactly One Java Path!

Win key + Edit the system environment variables. Check path variable. There must be exactly one path to Java in both system (recommended) and user path. 

Tested with:

`JAVA_HOME=C:\Program Files\Microsoft\jdk-17.0.0.35-hotspot`

### Verify Installations

```PowerShell
git --version
java -version
mvn -v
code -v
```

-----


## Important Concepts

- [Apache Beam](https://beam.apache.org/)
- [Overview](https://beam.apache.org/get-started/beam-overview/)
- SDKs (softare development kits)
- Pipeline Runners
- [Tour of Beam](https://beam.apache.org/get-started/tour-of-beam/)
- Basics: data pipeline, PCollection, PTransform
- Transforms: Map, FlatMap, Filter, Combine, GroupByKey
- Read/Write: ReadFromText, WriteFromText
- Windowing (time intervals when streaming): GlobalWindow, FixedWindows, SlidingWindows, Sessions.


## Create the Maven Archetype Project in Class Folder (e.g. 44517)

```PowerShell
mvn archetype:generate 
 -D archetypeGroupId=org.apache.beam 
 -D archetypeArtifactId=beam-sdks-java-maven-archetypes-examples 
 -D archetypeVersion=2.34.0 
 -D groupId=org.example 
 -D artifactId=word-count-beam 
 -D version="0.1" 
 -D package=org.apache.beam.examples 
 -D interactiveMode=false
 ```

This will create a subfolder word-count-beam. 

## In the new project, add sample data. 

Change directory into this new folder with `cd word-count-beam`.

Create sample.txt with text of your choice. Counting the occurances of each word is a way to gain understanding about a large text corpus. 

## Execute using the Direct runner

```PowerShell
mvn compile exec:java -D exec.mainClass=org.apache.beam.examples.WordCount `
 -D exec.args="--inputFile=sample.txt --output=counts" -P direct-runner
```

## Inspect Results

```PowerShell
ls counts*
```

## Explore

- Are the results useful yet? Why or why not?
- What dependencies are used? Hint: check pom.xml
- What is the main file that we just ran? Hint: check the execution command
- Where is it located (the path)? Hint: check src folder
- Where does the execution of this file begin? Hint: public static void main()
- Open WordCount.java and explore the code. 
- What is its package?
- What (free!) classes are imported?
- What is the class name? 
- Must the class name (WordCount) match the file name (WordCount.java)? 
- What 3 classes are defined? What do they extend?
- How are the Options defined? What does this interface extend?
- How many arguments does the runWordCount() function take? What type is it? Does it return anything? 
- What does the local variable p represent?
- What does the first p.apply() do?
- What does the second p.apply() do?
- What does the third p.apply() do?
- What does the fourth p.apply() do?
- After transforming, what do we call? 
- After p.run(), what do we call?
- How do we prepare and call our runWordCount() function?

## Learn More

- [Apache Beam WordCount Examples
](https://beam.apache.org/get-started/wordcount-example/)


## Objectives

- Be able to design pipelines to create value from data.
- Start with data sources.
- Plan & implement transformations. Must be able to be run in parallel. Runner may assign multiple machines to each step. Understand and apply basic big data functions including 
  - flat map
  - map
  - filter
  - group by key (reduce)
- Plan & create useful sinks. Output processed results into useful formats.

These skills are critical in big data. The exact tools, languages, runners, engines will change and evolve. Whatever language or tools you use, be able to generate value by using these critical transformations: flat map, map, filter, reduce (group by key).
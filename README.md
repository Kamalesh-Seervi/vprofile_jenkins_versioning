# vprofile_jenkins_versioning
Versioning 

# Tasks

- Versioning 


## Lets start configuring the version:

- After the success build go to Build Steps which is in configuration
- add few bash scripts for make a proper version ID 

```
mkdir -p versions
cp target/vprofile-v2.war versions/vprofile-V$BUILD_ID.war
```
- Reference: ``` https://www.jenkins.io/doc/pipeline/steps/pipeline-build-step/ ```
- Try 3 or many builds you will get with proper version naming:

<img width="1552" alt="image" src="https://github.com/Kamalesh-Seervi/vprofile_jenkins_versioning/assets/107933310/beb48541-2151-4b77-9a42-8d389336a12e">

--------------------------------------------------------------------------------------------------------------------------------------------

### Now lets create build with parameter :

- The use of of build with parameter is instead of automatic build ID we can use manual VERSION ID by getting input from thr user:
- Go to configure -> general -> check This project is parameterized -> add parameter -> string parameter

<img width="1552" alt="image" src="https://github.com/Kamalesh-Seervi/vprofile_jenkins_versioning/assets/107933310/91192d9a-184f-4da4-927b-67c366fddc1d">

- Now it will show build with parameter:

<img width="1552" alt="image" src="https://github.com/Kamalesh-Seervi/vprofile_jenkins_versioning/assets/107933310/dfaa7427-40ed-4385-865d-b0e71548663a">

- Thus now it works:

<img width="1552" alt="image" src="https://github.com/Kamalesh-Seervi/vprofile_jenkins_versioning/assets/107933310/50f7d623-5a86-4e97-bc4e-f24b80967bf9">

# NOTE: Try avoiding taking input or parameters from user because during automation it breaks the flow of chain.

--------------------------------------------------------------------------------------------------------------------------------------------

### Another way to create proper version numbering by adding timestamps is using plug-ins : ( Welcome to powerhouse of jenkins :)

- From available plug-ins install zentimestamp.
- Then go to configure -> general -> checkout Change date pattern for the BUILD_TIMESTAMP (build timestamp) variable
- Paste the below format:
```
yyyy-MM-dd-HH_mm
```

- Under execute Shell paste the below bash

```
cp target/vprofile-v2.war versions/vprofile-V$BUILD_ID--$BUILD_TIMESTAMP.war
```

- Now build the project

<img width="1552" alt="image" src="https://github.com/Kamalesh-Seervi/vprofile_jenkins_versioning/assets/107933310/48355af5-de6c-47b4-9b10-eae2e483a1d1">

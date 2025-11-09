Tomcat & Jenkins: Quick setup guide
=================================

This project is packaged as a WAR and is configured to run on Java 21 and Jakarta Servlet API (Jakarta EE 10).

Files added to support CI/CD:
- `Jenkinsfile` — declarative pipeline that builds the WAR and deploys it to a local Tomcat installation (Windows).

Prerequisites on the machine running Jenkins
- Java 21 installed and accessible to Jenkins (already present on your laptop).
- Maven (3.6+) installed or use the Jenkins Maven tool.
- Tomcat 10.1.x (or newer) installed for Jakarta servlet compatibility.

Prepare Tomcat
1. Extract Tomcat (e.g., `C:\apache-tomcat-10.1.x`).
2. Make sure Tomcat user has permission to read/write the `webapps` folder.
3. Optionally configure Tomcat users / manager if you want to use manager-based deployment.

Using the Jenkinsfile (recommended)
1. In Jenkins, create a new Pipeline job (or Multibranch Pipeline).
2. Point the job to this repository (SCM: Git) and make sure Jenkins checks out the repo.
3. In the job's Build Parameters, set `TOMCAT_HOME` to your Tomcat path (for example `C:\apache-tomcat-10.1.14`) and leave `CONTEXT_NAME` as `GreenDookan`.
4. Run the job. The pipeline will:
   - mvn -B -U -DskipTests clean package
   - copy `target/modern-webapp-1.0.0.war` to `%TOMCAT_HOME%\webapps\GreenDookan.war`
   - call `%TOMCAT_HOME%\bin\shutdown.bat` and then `%TOMCAT_HOME%\bin\startup.bat` to restart Tomcat.

Manual local run (without Jenkins)
1. Build locally:
   ```powershell
   Set-Location -Path 'C:\Users\DELL\Downloads\pblj'
   mvn -U -DskipTests clean package
   ```
2. Copy the WAR to Tomcat's webapps and start Tomcat:
   ```powershell
   Copy-Item 'C:\Users\DELL\Downloads\pblj\target\modern-webapp-1.0.0.war' -Destination 'C:\path\to\tomcat\webapps\GreenDookan.war' -Force
   Set-Location 'C:\path\to\tomcat\bin'
   .\startup.bat
   ```
3. Open the demo page:
   - http://localhost:8080/GreenDookan/greendookan-demo.html

Troubleshooting
- If you see ClassNotFoundException for `javax.servlet.*`, you're using an older Tomcat (9 or earlier). Install Tomcat 10.1.x.
- Check Tomcat logs in `%TOMCAT_HOME%\logs` (catalina, localhost logs) for details.
- If the Jenkins agent cannot access `%TOMCAT_HOME%`, give the Jenkins service user appropriate permissions or deploy via Tomcat Manager with credentials.

Next improvements
- Add Tomcat Manager or Cargo plugin deployment for zero-downtime deploys.
- Add automated smoke tests (HTTP checks) to the Jenkins pipeline.
- Add secure credentials handling in Jenkins (store `TOMCAT_HOME` as a secret or use credentials for manager deploy).

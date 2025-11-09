pipeline {
  agent any
  parameters {
    string(name: 'TOMCAT_HOME', defaultValue: 'C:\\Program Files\\Apache Software Foundation\\Tomcat 10.1', description: 'Full path to Tomcat installation (Windows).')
    string(name: 'CONTEXT_NAME', defaultValue: 'GreenDookan', description: 'Name of the webapp context (folder and war name).')
  }

  environment {
    MAVEN_OPTS = '-Xmx1g'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        echo 'Building with Maven...'
        bat 'mvn -B -U -DskipTests clean package'
      }
    }

    stage('Deploy to Tomcat') {
      steps {
        script {
          def builtWar = fileExists('target/modern-webapp-1.0.0.war') ? 'target/modern-webapp-1.0.0.war' : findFiles(glob: 'target/*.war')[0].path
          echo "Deploying ${builtWar} to ${params.TOMCAT_HOME}"

          // Stop Tomcat, remove exploded dir, copy WAR, start Tomcat
          bat "\"${params.TOMCAT_HOME}\\bin\\shutdown.bat\" || echo Tomcat shutdown returned non-zero"
          bat "IF EXIST \"${params.TOMCAT_HOME}\\webapps\\${params.CONTEXT_NAME}\" rd /s /q \"${params.TOMCAT_HOME}\\webapps\\${params.CONTEXT_NAME}\""
          bat "copy /Y \"${builtWar}\" \"${params.TOMCAT_HOME}\\webapps\\${params.CONTEXT_NAME}.war\""
          bat "\"${params.TOMCAT_HOME}\\bin\\startup.bat\""
          echo 'Deployed and started Tomcat. Give Tomcat a few seconds to expand the WAR.'
        }
      }
    }

    stage('Smoke Test') {
      steps {
        echo 'Smoke test: check if demo page is reachable (manual verification recommended).'
        echo "Open: http://localhost:8080/${params.CONTEXT_NAME}/greendookan-demo.html"
      }
    }
  }

  post {
    success {
      echo 'Pipeline succeeded.'
    }
    failure {
      echo 'Pipeline failed. Check the console output and Tomcat logs.'
    }
  }
}

pipeline { 

  agent any 

  options { 

    buildDiscarder logRotator(numToKeepStr: '3') 

  } 

  environment { 

    GIT_REPO = "https://github.com/baruas42/java-gradle.git" 

    ROOT_WAR_LOCATION = "/opt/tomcat/webapps" 

    LOCAL_WAR_FILE = "build/libs/my-web-app.war" 

    TOMCAT_BIN_DIR = "/opt/tomcat/bin" 

    GRADLE_PATH = "/usr/local/gradle/gradle-8.11/bin/gradle" 

  } 

  stages { 

    stage('Checkout Code') { 

      steps { 

        // Clone the GitHub repository 
        git branch: 'main', url: "$GIT_REPO" 

      } 

    } 

    stage('Build with Gradle') { 

      steps { 

        // Run Gradle clean and build to generate the WAR file 
        sh '$GRADLE_PATH clean build' 

      } 

    } 

    stage('Verify WAR File') { 

      steps { 

        // Check if the WAR file was successfully built 
        sh 'ls -la build/libs' 

        sh 'if [ ! -f "$LOCAL_WAR_FILE" ]; then echo "WAR file not found: $LOCAL_WAR_FILE"; exit 1; fi' 

      } 

    } 

    stage('Deploy WAR to Tomcat') { 

      steps { 

        // Stop Tomcat server 
        sh 'sudo $TOMCAT_BIN_DIR/shutdown.sh || true' 

 
        // Remove previous deployment 
        sh 'sudo rm -rf $ROOT_WAR_LOCATION/ROOT; sudo rm -f $ROOT_WAR_LOCATION/ROOT.war' 


        // Copy the new WAR file to the Tomcat webapps directory 
        sh 'sudo cp $LOCAL_WAR_FILE $ROOT_WAR_LOCATION/ROOT.war' 


        // Set correct permissions for the WAR file 
        sh 'sudo chown tomcat:tomcat $ROOT_WAR_LOCATION/ROOT.war' 


        // Start Tomcat server 
        sh 'sudo $TOMCAT_BIN_DIR/startup.sh' 

      } 

    } 

  } 

} 

node("jenkins-slave")
{ 
 def mvnHome = '/opt/apache-maven-3.9.4/'
 stage("SCM Checkout")
 { 
  checkout scm
 }

    stage('Build') {
         // Run the maven build
        if (isUnix()) {
            sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
        } else {
            bat (/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
        }
    }
    stage('Results') {
          archive 'target/*.war'
    } 
    stage('deploy') {
      sh "cp -p **/*.war /opt/apache-maven-3.9.4"
      }
      
   }  

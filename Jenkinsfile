node{
      def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
            sshagent(['Tomcat-jenkins']) {
               sh sshpass -p "guna1" scp target/*.war guna1@172.17.0.3:/home/guna1/Softwares/apache-tomcat-8.5.34/webapps
               sh sshpass -p "guna1" ssh -o StrictHostkeyChecking=no guna1@172.17.0.3 "JAVA_HOME=/home/guna1/Softwares/jdk1.8.0_181" "/home/guna1/Softwares/apache-tomcat-8.5.34/bin/startup.sh"
          }
         
     }
      
 }

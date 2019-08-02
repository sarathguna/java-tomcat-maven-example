node{
      def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "$/home/guna1/Softwares/apache-maven-3.5.4/bin/mvn clean package -Dmaven.test.skip=true"
      }
      
      stage('Deploy') {     
            sshagent(['Tomcat-jenkins']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war guna2@172.17.0.5:/home/guna2/Softwares/apache-tomcat-8.5.34/webapps'
          }
         
     }
      
 }

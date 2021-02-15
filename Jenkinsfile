node {
    def mavenhome = tool name: "maven3.6.3"
    stage('CheckoutCode')
    {
        git branch: 'development', credentialsId: '961c3ce7-6752-4eb6-b24d-15e5ced7e23d', url: 'https://github.com/kalluri126/application-web.git'
    }
    stage('Build')
    {
        sh "${mavenhome}/bin/mvn clean package"
    }
    stage('deploy code into tomcart')
    {
        sshagent(['fa70ae93-8d71-44c3-bc02-c6b0a76e0de0']) {
            sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war ec2-user@13.59.32.141:/opt/apache-tomcat-9.0.41/webapps"
}
    }
}

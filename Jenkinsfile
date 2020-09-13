pipeline {
    agent {
        docker {
            image 'php:7.3'
            args '-u root:sudo'
        }
    }
    environment {
        CI=true
    }
    stages { 
        stage('Build') {
            steps { 
                sh 'apt-get update -y && apt-get install -y libxml2-dev && apt-get install -y git'
                sh 'curl -sS https://getcomposer.org/installer -o composer-setup.php'
                sh 'php composer-setup.php'
                sh 'php composer.phar install'
            }
        }
        stage('Test') {
            steps { 
                sh './vendor/bin/phpunit'
            }
        } 
    }
    post {
         always {  
             echo 'This will always run'  
         }  
         success {  
            mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "Success build CI: Project name -> ${env.JOB_NAME}", to: "tiagorosadacost@gmail.com";  
         }  
         failure {  
            mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "tiagorosadacost@gmail.com";  
         }  
    }
}
 
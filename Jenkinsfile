pipeline {
    agent {
        docker {
            image 'php:7.3'
        }
    }
    environment {
        CI=true  
        HOME = '.'
    }
    stages { 
        stage('Build') {
            steps { 
                sh 'apt-get update -y && apt-get install -y libxml2-dev && apt-get install git'
                sh 'curl -sS https://getcomposer.org/installer -o composer-setup.php'
                sh 'php composer-setup.php'
                sh 'php composer.phar install'
            }
        }
      
    }
}
 
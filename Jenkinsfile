pipeline {
    agent {
        docker {
            image 'php:7.3'
            args '-u root:sudo'
        }
    }
    options {
        skipDefaultCheckout true
    }
    environment {
        CI=true
    }
    stages { 
        stage('Build') {
            steps { 
                checkout scm
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
}
 
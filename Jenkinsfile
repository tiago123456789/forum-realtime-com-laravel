pipeline {
    agent {
        docker {
            image 'php:7.3'
            args '-u root:sudo'
        }
    }
    stages { 
        stage('install packages necessaries') {
            steps { 
                sh 'apt-get update -y && apt-get install -y libxml2-dev && apt-get install -y git'
                sh 'curl -sS https://getcomposer.org/installer -o composer-setup.php'
                sh 'php composer-setup.php'
            }
        }
        stage('Build') {
            steps { 
                sh 'php composer.phar install'
            }
        }
        stage('Tests') {
            steps { 
                sh './vendor/bin/phpunit'
            }
        }
    }
    
}
 
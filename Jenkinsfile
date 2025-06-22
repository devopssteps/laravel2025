pipeline {
    agent {
     node {
         label "laravel"
     }
 }
  stages {
        stage('checkout') {
              steps {
                  git branch: 'main', url: 'https://github.com/devopssteps/laravel2025.git'
              }
        }
        //Build stage
          stage('Build') {
            steps {
                sh 'composer install'
                sh 'npm install'
                sh 'npm run build'
                // if we need any other commands to compile
            }
         }
        //Test stage
        stage('Test') {
            steps {
                sh 'php artisan test'
            }
        }
        // deploy to production 
        stage('Deploy to production') {

            steps {
                sh 'ssh ubuntu@50.19.206.170 -o StrictHostKeyChecking=no "bash /var/www/larademo/scripts/deploy.sh" '
            }
        }  
   }

}
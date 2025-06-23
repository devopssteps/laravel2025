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
        // deploy to staging 
        stage('Deploy to stgaing') {

            steps {
                sh 'ssh ubuntu@54.242.14.213 -o StrictHostKeyChecking=no "bash /var/www/larademo/scripts/deploy.sh" '
            }
        } 
        // deploy to production server 
        stage('Deploy to production') {
            input {
                message "Want to deploy to production"
                ok "Yes"
            }

            steps {
                sh 'ssh ubuntu@50.19.206.170 -o StrictHostKeyChecking=no "bash /var/www/larademo/scripts/deploy.sh" '
            }
        }  
   }

}

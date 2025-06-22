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
  }

}
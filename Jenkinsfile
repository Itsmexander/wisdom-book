pipeline {
     agent {
          docker {
               image 'maven:3-jdk-11'
               args '-p 33333:8090'
          }
     }
     environment {
          HOME = '.'
     }
     stages {
          stage('Source') {
               steps {
                    git branch: 'main',
                        url: 'https://github.com/ladyusa/wisdom-book'
               }
          }
          stage('Build') {
               steps {
                    sh 'mvn package -DskipTests'
               }
          }
          stage('Test') {
               steps {
                    echo 'testing...'
               }
          }
          stage('Deploy') {
               steps {
                    sh 'java -jar ./target/book-1.0.jar'
               }
          }
     }
}

node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Build'){
        sh 'composer install --no-scripts --prefer-dist --no-dev --ignore-platform-reqs'
    }
    
    stage('Docker Build') {
        sh 'docker build -t miltonfoliveira/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push miltonfoliveira/laravel:$BUILD_NUMBER'
        sh 'docker rmi -f miltonfoliveira/laravel:$BUILD_NUMBER'
    }
}

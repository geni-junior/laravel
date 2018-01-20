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
    
    stage('config') {
        parallel(
            'config cache': {
                echo 'Era so pra instalar um jenkins'
                }
        )
    }
    stage('Docker Build') {
        sh 'docker build -t genijunior/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push genijunior/laravel:$BUILD_NUMBER'
    }
}

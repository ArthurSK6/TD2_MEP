pipeline {
    agent any

    stages {

        stage('build') {
            steps {
                echo 'Building..'
                
                
                sh 'docker build -t arthursk/mep_td2_hurdebourg:latest .'                
            }
        }
        stage('Docker Push') {
            steps {
                echo ' Docker push'
                
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"

                    // Push uniquement l'image du backend
                    sh 'docker push arthursk/mep_td2_hurdebourg:latest'
            }
        }
    }
}

pipeline {

    agent any


    stages {

        stage('Stop Docker Container') {

            steps {

                sshagent(['ubuntu_docker']) {

                    sh '''

                    ssh -o StrictHostKeyChecking=no ubuntu@54.82.85.32 "

                    docker stop fruitkha-website || true

                    docker rm fruitkha-website || true

                    "

                    '''

                }

            }

        }


        stage('Verify Container') {

            steps {

                sshagent(['ubuntu_docker']) {

                    sh '''

                    ssh -o StrictHostKeyChecking=no ubuntu@54.82.85.32 "

                    docker ps -a

                    "

                    '''

                }

            }

        }

    }

}

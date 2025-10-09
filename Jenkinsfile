@Library('shared-library') _
pipeline {
    agent { label "fedora-agent" }

    stages {
        stage('Cloning the repo') {
            steps {
                script{
                    clone("https://github.com/KrishnaPathak824/Blog-App.git","main")
                }
            }
        }
        stage('frontend-build') {
            steps{
                script{
                    build('frontend','blog-app-frontend')
                }
            }
        }
        stage("Push to DockerHub")
        {
            steps{
                script{
                    tagandpush('blog-app-frontend')
                }
            }
        }
        stage("Deploy") {
            steps {
                script{
                    run('blog-app-frontend','frontend-app')
                }
            }
        }
    }
}

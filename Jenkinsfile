pipeline{
    environment{
        BUILD_NUM=''
    }
    agent any
    
    stages{
        stage("Cloning Code"){
            steps{
            git branch: "master",url: 'https://github.com/calebkingeno03/gallery.git'
            }
        }
        stage("Install code"){
            steps{
                sh 'npm install'
            }
        }
        // stage("Test Code"){
        //     steps{
        //         sh 'npm test'
        //     }
        // }
        stage("Deployment of Code"){
            steps{
                sh 'npm run'
                
            }
        }
        stage("User Notification"){
            steps{
                slackSend color: 'good', message: "Build N°: ${env.BUILD_NUMBER} was successfully deployed in 'https://gallery-2.onrender.com/'"
            }
        }
    
     post{
        always{
            emailext(
                subject: 'Deplyment Status.${BUILD_STATUS}',
                body: '''<html>
                            <body>
                                <p>Build Status:${BUILD_STATUS}</p>
                                <p>Build Number:${BUILD_NUMBER}</p>
                                <p>Check <a href='${BUILD_URL}'> output.</a></p>
                            </body>
                </html>''',
                to:'calebroykoech03@gmail.com',
                from:'calebroykoech03@gmail.com',
                replyTo:'calebroykoech03.com',
                mimeType:'text/html'
            )
        }

    }  
 }  

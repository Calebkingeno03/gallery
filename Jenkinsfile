pipeline{
    environment{
        BUILD_NUM=''
    }
    agent any
    // tools{
    //     nodejs 'node'
    // }
    stages{
        stage("Clone Code"){
            steps{
            git branch: "master",url: 'https://github.com/niconyango/gallery.git'
            }
        }
        stage("Installing Dependencies"){
            steps{
                sh 'npm install'
            }
        }
        // stage("Test Code"){
        //     steps{
        //         sh 'npm test'
        //     }
        // }
        stage("Deploy Code"){
            steps{
                sh 'npm run'
                // echo 'Deploying the code' 
                
            }
        }
        stage("User Notification"){
            steps{
                //slackSend color: 'good',message:'Deployment Successful'
                slackSend color: 'good', message: "Build N°: ${env.BUILD_NUMBER} was successfully deployed in 'https://gallery-2.onrender.com/'"
            }
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
                replyTo:'calebroykoech03@gmail.com',
                mimeType:'text/html'
            )
        }

    }  
}

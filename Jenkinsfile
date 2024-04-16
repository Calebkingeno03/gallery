
pipeline{
    environment{

    }
    agent any
 
    stages{
        stage("Clone Code"){
            steps{
            git branch: "master",url: 'https://github.com/Calebkingeno03/gallery.git'
            }
        }
        stage("Install Dependencies"){
            steps{
                sh 'npm install'
            }
        }
        // stage("Test stage"){
        //     steps{
        //         sh 'npm test'
        //     }
        // }
        stage("Deploy stage"){
            steps{
                sh 'npm run'
                
            }
        }
    } 
}

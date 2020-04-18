pipeline{
    agent any
    environment{
        VERSION = '1.0.0'
    }
    stages{
        stage("Build"){
            steps{
                echo "builidng my application"
                echo "version of this file are ${VERSION}"
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying my application"
            }
        }
    }
}

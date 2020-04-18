pipeline{
    agent any
    environment{
        VERSION = '1.0.0'
    }
	parameters{
		choice{name: 'VERSION1', choices: ['1.0.0','2.0.0','3.0.0'], description: 'version control'}
		booleanParam{name: 'TEST', defaultValue: true, description: 'for testing'}
    stages{
        stage("Build"){
            steps{
                echo "builidng my application"
                echo "version of this file are ${VERSION}"
				echo "parameters ${params.VERSION1}"
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying my application"
            }
        }
    }
}

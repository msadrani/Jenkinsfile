pipeline{
    agent any
	def gv
    environment{
        VERSION = '1.0.0'
    }
	parameters{
		choice(name: 'VERSION1', choices: ['1.0.0','2.0.0','3.0.0'], description: 'version control')
		booleanParam(name: 'TEST', defaultValue: true, description: 'for testing')
	}
    stages{
        stage("Build"){
            steps{
				script{
					gv = load "script.groovy"
					gv.buildapp()
				}
            }
        }
        stage("Deploy") {
		when {
			expression{
				params.TEST
			}
		}
            steps{
                script{
					gv.deployapp()
				}
            }
        }
    }
}

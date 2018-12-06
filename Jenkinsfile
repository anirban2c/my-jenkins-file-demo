pipeline {
    agent any
    stages {
        stage('One') {
            steps {
                echo 'Hi, This is Anirban from India'
            }
        }
        stage('Two') {
            steps {
                input ('Do you want to proceed?')
            }            
        }
        stage('Three') {
            when {
                  not {
		        branch 'master'
		      }
            }
            steps {
                echo 'Hello'
            }  
	    }
        stage('Four') {           
            parallel {
                stage('unit test') {
                    steps {
                        echo 'Running the unit test'
                    }
                }
                stage('integration test') {
                    agent {
                    docker {
                        reuseNode false
                        image 'ubuntu'
                    }
                    }
                    steps {
                        echo 'Running my integration test'
                    }                 
                }
            }
        }
    }
}

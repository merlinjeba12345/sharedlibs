pipeline{
    agent any
        stage('One'){
            steps{
                echo 'Hi this is Declarative pipeline'
            }
        }
       stage('Two'){
            steps{
                input('Do you want to proceed?')
            }
        } 
        stage('Three'){
            steps{
                when{
                    not{
                        branch "master"
                    }
                    steps{
                        echo "hello"
                    }
                }
            }
        }
        stage('Four'){
            parallel{
                stage('Unit Test'){
                    steps{
                        echo "Running the Unit test"
                    }
                }
                stage('Integration Test'){
                    agent {
                        docker{
                            reuseNode False
                            image 'ubuntu'
                        }
                    }
                    steps{
                        echo "Running the Integration Test"
                    }
                }
            }
            
        }
    }


pipeline {
    agent any    

    stages {


         stage("downloading Success") {
            steps {
                script {
                  echo "downloading has been executed successfully"                  
                }
            }
        }


        stage("Extracting") {
            steps {
                script {
                  echo "extracting files and data for wordpress/mysql"
                  sh '7z x wordmysqlpma_data.7z -aoa -o$PWD'                  
                }
            }
        }


        stage("preparing") {
            steps {
                script {
                   echo "cleaning up previous docker files"
                //    sh 'docker-compose -f compose.yaml down'
                }
            }
        }
       

        stage("deploying environment") {
            steps {
                script {
                    echo "using docker compose file to deploy environment"
                    sh 'docker-compose -f compose2.yaml up -d'                  
                }
            } 
        }        
        
        
    }   
}
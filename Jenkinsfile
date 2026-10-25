
pipeline {                                    

    agent any                                 

    environment {                             
        PATH = "/opt/maven/bin:$PATH"         
    }                                         

    stages {                                  

        stage("build") {                      
            steps {                            
                echo "----------- build started ----------"  
                                             
                sh 'mvn clean deploy -Dmaven.test.skip=true'  
                                              
                echo "----------- build completed ----------"  
                                              
            }                                 
        }                                     

        stage("test") {                       
            steps {                           
                echo "----------- unit test started ----------"  
                                              // Logs a message indicating the start of unit tests
                sh 'mvn surefire-report:report'  
                                              // Runs the Maven Surefire report to execute unit tests
                echo "----------- unit test completed ----------"  
                                              
            }                                 
        }                                     

        stage('SonarQube analysis') {         
            environment {                     
                scannerHome = tool 'SonarQube-Scanner'  
                                              
            }                                 

            steps {                           
                withSonarQubeEnv('SonarQube') {  
                                              
                    sh "${scannerHome}/bin/sonar-scanner"  
                                              
                }                             
            }                                 
        }                                     
											  
    }                                         
}                                             


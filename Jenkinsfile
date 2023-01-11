pipeline{
    agent any
    tools { 
        maven 'maven3'
    }
    stages
       {
            stage("clean")
            {
                steps{
                    sh "mvn clean"
                }

            }
            stage("Build")
            {
                steps{
                   sh "mvn compile"
                }
            }
            stage("TEST")

            {
                steps{
                    sh "mvn test"

                }

            }

            stage("package")

            {




                steps{




                    sh "mvn package"




                }




            }

        stage('Ok') 

           {

            steps {

                echo "Ok"

            }

           }
            stage('Parallel and archiving') {
          parallel {

            stage('Test'){
              steps {
               sh 'mvn test'
              }
            }
             stage('Archiving') {
              steps {
               sh 'echo "Artifact" > test1.txt'
                archiveArtifacts artifacts: 'test1.txt'
                }
              }
          }
        }

       }

    

    post {

        always {

            emailext body: 'abcd', subject: 'abcd', to: 'meenakshi.goyal@knoldus.com'

           }

    }
}


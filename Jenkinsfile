
pipeline{
    agent any
     options {
    quietPeriod(120)
    // more options
  }
    stages{
        stage('git checkout')
        {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sunny255005/employeeSpringBoot.git']]])
            }
        }
        stage('run mvn'){
            steps{
                echo "mvn clean package"
            }
            
        }
                 stage('Confirm for unit tests') {
                    steps {
                       script{
                           def is_unit_test_continue_parameter = input(id: 'is_unit_test_continue', message: 'Do you want to go for unit tests and jacoco reports?',

                            parameters: [[$class: 'ChoiceParameterDefinition', defaultValue: 'No',

                                description:'Unit Test choices', name:'unit tests and jacoco report', choices: 'Yes\nNo']

                            ])

                            is_unit_test_continue=is_unit_test_continue_parameter

                       }}}

                stage('Unit Tests & Jacoco Reports') {

                    when {

                 expression { is_unit_test_continue == "Yes" }

                }

             steps {

                 echo "Hello,unit_test continue...!"

                    script {

                       

                        echo 'testing in progess...'

                    }

                }

                }

                 stage('Confirm for Sonarqube Check') {

                    steps {

                       script{

                           def is_sonarqube_parameter = input(id: 'is_sonarqube', message: 'Do you want to continue with Sonarqube?',

                            parameters: [[$class: 'ChoiceParameterDefinition', defaultValue: 'No',

                                description:'Sonarqube choices', name:'sonarqube_choice_params', choices: 'Yes\nNo']

                            ])

                           is_sonarqube=is_sonarqube_parameter

                       }}}

             stage('Sonarqube Integeration') {

                    when {

                 expression { is_sonarqube == "Yes" }

             }

             steps {

                 echo "Hello,sonarqube continue...!"

                 

                }

                        }
      
    }
    
}

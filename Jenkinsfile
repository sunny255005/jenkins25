
pipeline{
    agent any
    options{
     quietPeriod(760)
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
                sh 'mvn clean package'
            }
            
        }
      
    }
    
}

pipeline{

    agent any
    environment{
  
        PATH = "/opt/maven/apache-maven-3.6.3/bin:$PATH"
    }
    stages{
        stage("SCM Checkout")
        {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ValaxyTech/hello-world.git']]])
            }
            
        }
        stage("Maven Build"){

            steps{
                sh "mvn clean package"
            }
        }

    }
}

currentBuild.displayName = "LeanJenkins#"+currentBuild.number

pipeline{

    agent any
    properties([parameters([choice(choices: 'master\nmain\nTest1', description: '', name: 'Branch')])])
    environment{
  
        PATH = "/opt/maven/apache-maven-3.6.3/bin:$PATH"
    }
    stages{
        stage("SCM Checkout")
        
        {
            
            steps{
                echo "Selected Branch {params.Branch}"
                checkout([$class: 'GitSCM', branches: [[name: '*/{params.Branch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ValaxyTech/hello-world.git']]])
            }
            
        }
        stage("Maven Build"){

            steps{
                sh "mvn clean package"
            }
        }

    }
}

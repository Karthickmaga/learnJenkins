currentBuild.displayName = "LeanJenkins#"+currentBuild.number

pipeline{

    agent any
        environment{
  
        PATH = "/opt/maven/apache-maven-3.6.3/bin:$PATH"
    }
    stages{
        
        stage("Setting Parameter"){
                             steps{
                                        script { 
                    properties([
                        parameters([
                            choice(
                                choices: ['master', 'main', 'Test'], 
                                name: 'Branch')])])
                                        }            
                                }
                                
              }
        stage("SCM Checkout")
        
        {
            
            steps{
                echo "Selected Branch ${params.Branch}"
                checkout([$class: 'GitSCM', branches: [[name: "${params.Branch}"]], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/ValaxyTech/hello-world.git']]])
            }
            
        }
        stage("Maven Build"){

            steps{
                sh "mvn clean package"
            }
        }

    }
}

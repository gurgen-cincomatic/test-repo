pipeline {
   agent any
   parameters {
        gitParameter name: 'Version',
            defaultValue: 'origin/Main',
            type: 'PT_TAG'
   }
   stages{
      stage('Checkout project'){
         steps{
            checkout([$class: 'GitSCM',
                                      branches: [[name: "${params.Version}"]],
                                      doGenerateSubmoduleConfigurations: false,
                                      extensions: [],
                                      gitTool: 'Default',
                                      submoduleCfg: [],
                                      userRemoteConfigs: [[url: 'https://github.com/gurgen-cincomatic/test-repo.git']]
                                    ])

            sh "ls -lat"
       }
   }

      stage('login server'){
         steps{
            sshagent(credentials:['web-front-lt01']){
               sh 'ssh  -o StrictHostKeyChecking=no  root@10.10.0.56 uptime "whoami"'
          }
        echo "success lgoin"
         }
       }

        }
   }
}
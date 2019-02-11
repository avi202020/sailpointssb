pipeline{
agent any
environment{
    SPTARGET='sandbox'
}
stages{

    stage('scm'){

        steps{
            echo 'checking out'
            checkout([$class: 'GitSCM', branches: [[name: '*/jenkins']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '447f833f-500c-4a0c-a4dd-2a90bb95c20b', url: 'https://github.com/ets9282/sailpointssb.git']]])

        }
    }
    stage('build'){
        steps{
            echo 'building Tomcat war'
            sh 'cp /home/vagrant/ssb/base/ga/identityiq-7.3.zip $WORKSPACE/base/ga'    
            withAnt(installation: 'Myant') {
                sh 'ant down clean cleanWeb main deploy up'
        }

        }
    }
}

}

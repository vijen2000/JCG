//import com.att.sdt.Utilities

#!groovy

pipeline{
agent any
options {
    buildDiscarder(logRotator (daysToKeepStr: '10',numToKeepStr: '30'))
    skipDefaultCheckout true
}
tools {
    jdk 'jdk1.8'
}

environment {
    APPNAME = "Test ANT"
    APP_ALIAS_NAME = "ANT_TEST"
    DEBUG_FLAGS = '-g'
    //DEPLOY_TO = "${params.CDA_ENV_OPTION}"       
}
stages{
    stage("Checkout"){
	
	steps{
            echo 'Source Checkout'
			checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'git1.9', submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'GitHUB', url: 'https://github.com/vijen2000/JCG.git']]])
		}
	}
}	
stages{
	stage ("Compile"){
			
			echo 'Compiling the code'
			ant 
		}
}
pipeline {
  agent any
  tools { 
        maven 'Maven_3_8_4'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=udayvarma_varmabuggywebapp -Dsonar.organization=udayvarma -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=460a499e8d80d82171867e00ff438d6b13f420c2'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'd9e70fa5-d626-4979-bf38-6199fce20b42 ', variable: 'd9e70fa5-d626-4979-bf38-6199fce20b42 ')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}

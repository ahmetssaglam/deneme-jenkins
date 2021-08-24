pipeline {
	agent any
  
	stages {
		stage('build') {
        		steps {
	  			 //sh 'cd'
          			//sh 'cd GitHub-Projects/deneme-jenkins/'
				echo 'Build'
				sh 'git config --global user.email "ahmetssaglam@gmail.com"'
				sh 'git config --global user.name "ahmetssaglam"'
        		}
      		}
	    	stage('preparation-test') {
	      		steps {
		      		sh 'pip3 install pytest'
		      		echo 'Pytest Installed'
	     		}
	    	}
	    	stage('test') {
	      		steps {	
		      		script {
			      		try {
			      			sh 'python3 -m pytest tests'
			      			echo 'Test Passed !'
		      			}
		      			catch (err) {
				
				      		echo 'commiIIt'
						
            					//git url: "git@github.com:ahmetssaglam/flask-docker-tdd.git",
               					// credentialsId: 'bdefd814-cf0d-4e6d-8a6a-08b00bd71ab1',
              					//  branch: 'dev'
				
				
						  sh 'git checkout dev'
						  sh 'git pull'
						  sh 'git log -1'
						  //sh 'git reset --hard dev@{1.minutes.ago}'
						  //sh 'git reset --hard HEAD~1'
						  withCredentials([usernamePassword(credentialsId: 'c93dd6e5-ea3a-44b4-a4d7-cbeb95f269fd', passwordVariable: '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', usernameVariable: 'ahmetssaglam')]) {
                        				sh('git push https://ahmetssaglam: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@github.com/ahmetssaglam/deneme-jenkins.git')
                   				 }
						  // sh 'git push -f origin dev'
						  echo 'Test Failed ! Changes Reverted !'
		    			}
				}
		    		echo 'Test Completed !'
			}
		}
	}
}

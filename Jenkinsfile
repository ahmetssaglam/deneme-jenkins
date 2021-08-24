pipeline {
	agent any
  
	stages {
		stage('build') {
        		steps {
	  			sh 'cd'
          			sh 'cd GitHub-Projects/deneme-jenkins/'
        		}
      		}
	    	stage('preparation-test') {
	      		steps {
		      		sh 'source ../../VirEnvs/testing-env/bin/activate'
		      		echo 'Virtual Env Activated'
	     		}
	    	}
	    	stage('test') {
	      		steps {
		      		echo 'Waiting for DB !!'
		       		// sh 'sleep 30'	
		      		script {
			      		try {
			      			sh 'python3 -m pytest tests'
			      			echo 'Test Passed !'
		      			}
		      			catch (err) {
				
				      		echo 'commit'
            					//git url: "git@github.com:ahmetssaglam/flask-docker-tdd.git",
               					// credentialsId: 'bdefd814-cf0d-4e6d-8a6a-08b00bd71ab1',
              					//  branch: 'dev'
				
				
						sh 'git checkout dev'
						//sh 'git reset --hard dev@{1.minutes.ago}'
						// sh 'git reset --hard HEAD~1'
						//sh 'git push -f origin dev'
						echo 'Test Failed ! Changes Reverted !'
		    			}
				}
		    		echo 'Test Completed !'
			}
		}
	}
}

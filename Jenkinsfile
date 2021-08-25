def res = "success"
pipeline {
	agent any
  
	stages {
		stage('build') {
        		steps {
	  			 //sh 'cd'
          			//sh 'cd GitHub-Projects/deneme-jenkins/'
				echo 'Build'
				sh 'python3 /plus/plus.py'
				//sh 'git config --global user.email "ahmetssaglam@gmail.com"'
				//sh 'git config --global user.name "ahmetssaglam"'
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
						
						  res = "fail"
				      		  echo 'cmt'
						  sh 'git checkout dev'
						  sh 'git pull'
						  sh 'git log -1'
						  //sh 'git reset --hard dev@{1.minutes.ago}'
						  sh 'git reset --soft HEAD~1'
						  echo 'Test Failed ! Changes Reverted !'
		    			}
					
					finally {
						if (res == "fail") {
						    withCredentials([gitUsernamePassword(credentialsId: 'b1916737-98ac-4bd5-a2fe-3c4725e5f71a', gitToolName: 'git-tool')]) {
							sh 'git push -f origin dev'
						    }
						} 
						else {
			    				echo 'Executed build and tests successfully finished!'
						}
		   		      }
					
				}
		    		echo 'Test Completed !'
			}
		}
	}
}

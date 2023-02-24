pipeline {
	agent any
	tools {
    	maven 'my_mvn'
	}
	stages {
    	stage("Checkout") { 
    	     agent{
        	        lable 'slave1-machine'
        	    }
        	steps {      
        	   git branch: 'session5.2_pipeline', url: 'https://github.com/anandch543/Jenkins-cicd.git'        	 
           	   stash name: 'stashed'
        	}    
    	}
    	stage('clean') {
    	    agent{
        	        lable 'slave2-machine'
        	    }
        	steps {
        	unstash 'stashed'
        	sh "mvn clean"  	 
        	}
    	}
    	stage('Build') {
    	    agent{
        	        lable 'slave2-machine'
        	    }
        	steps {
        	unstash 'stashed'
        	sh "mvn compile"  	 
        	}
    	}
   	 
    	stage("Unit test") {
    	    agent{
        	        lable 'slave2-machine'
        	    }
        	steps {
        	    unstash 'stashed'
            	sh "mvn test"          	 
       	}
}
}
}

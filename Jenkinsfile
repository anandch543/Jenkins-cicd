pipeline {
	agent any
	
	stages {
    	stage("Checkout") { 
    	     agent{
        	        label('slave1-machine')
        	    }
        	steps {      
        	   git branch: 'session5.2_pipeline', url: 'https://github.com/anandch543/Jenkins-cicd.git'        	 
           	   stash(name: 'workspace', useDefaultExcludes: false)
        	}    
    	}
    	stage('clean') {
    	    agent{
        	        label('slave2-machine')
        	    }
        	steps {
        	unstash('workspace')        	 
        	sh "mvn clean"  	 
        	}
    	}
    	stage('Build') {
    	    agent{
        	        label('slave2-machine')
        	    }
        	steps {
        	
        	sh "mvn compile"  	 
        	}
    	}
   	 
    	stage("Unit test") {
    	    agent{
        	      label ('slave2-machine')
        	    }
        	steps {
        	   	sh "mvn test"          	 
       	}
}
}
}

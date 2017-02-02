stage('SCM') {
    node{
        def URL = 'https://github.com/suibinz/CICD.git'
        echo "Build#${env.BUILD_ID}: git fetch: $URL" 
		git url: URL
    }
}

stage("Build") {
    node {
		def mvnHome = tool 'M3'
		sh "java -version"
		env.JAVA_HOME = tool "JDK"
        sh "$mvnHome/bin/mvn -v"
        echo "Build#${env.BUILD_ID}:Hello Stage Build"
        sh "ls && pwd && $mvnHome/bin/mvn -f App/simpleMaven/simple-maven-project-with-tests-master -B verify"
    }
}

stage("QA Test") {
    parallel master: {
		node("master") {
        	echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#1"
    	}
	}
//	master1: {
//		node("master") {
//        	echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#2"
//    	}
//	},
//	master1: {
//		node("master") {
//        	echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#3"
//    	}
//	}
}

stage("Manual Promotion") {
    node {
        mail (to: 'suibinzh@gmail.com', \
        subject: "Job '${env.JOB_NAME}' (${env.BUILD_NUMBER}) passed QA \
        awaiting for approval", \
        body: "Please go to ${env.BUILD_URL}.");
        def userInput = input( id: 'userInput', message: 'Pass Build and QA, Promote to Deployment?', \
        parameters: [[$class: 'TextParameterDefinition', defaultValue: 'Approver', \
        description: 'Environment', name: 'env'], \
        [$class: 'TextParameterDefinition', defaultValue: 'Approver', \
        description: 'Target', name: 'Promote Now']])
        echo ("Env: "+userInput['env'])
        echo ("Target: "+userInput['target'])
    }    
}

stage("Deploy") {
    node {
        echo "Build#${env.BUILD_ID}:Hello Stage Deploy"
    }
}

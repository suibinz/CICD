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
        sh "$mvnHome/bin/mvn -v"
        echo "Build#${env.BUILD_ID}:Hello Stage Build"
        sh "cd CICD/App/simpleMaven && pwd && $mvnHome/bin/mvn -B verify"
    }
}

stage("Test") {
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

stage("Deploy") {
    node {
        echo "Build#${env.BUILD_ID}:Hello Stage Deploy"
    }
}

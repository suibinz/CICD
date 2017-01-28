stage('SCM') {
    node{
        echo "Build#${env.BUILD_ID}:Hello Stage SCM" 
		sh "env"
    }
}

stage("Build") {
    node {
        echo "Build#${env.BUILD_ID}:Hello Stage Build"
    }
}

stage("Test") {
    parallel N1: {
		node {
        	echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#1"
    	}
	},
	N2: {
		node {
        	echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#2"
    	}
	},
	N3: }
		node {
        	echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#3"
    	}
	}
}

stage("Deploy") {
    node {
        echo "Build#${env.BUILD_ID}:Hello Stage Deploy"
    }
}

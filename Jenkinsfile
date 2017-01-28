stage('SCM') {
    node{
        echo "Build#${env.BUILD_ID}:Hello Stage SCM" 
		sh "env"
    }
}

stage("Build" {
    node {
        echo "Build#${env.BUILD_ID}:Hello Stage Build"
    }
}

stage("Test") {
    parallel node {
        echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#1"
    }
		node {
        echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#2"
    }
		node {
        echo "Build#${env.BUILD_ID}:Hello Stage Test in Th#3"
    }
}

stage("Deploy") {
    node {
        echo "Build#${env.BUILD_ID}:Hello Stage Deploy"
    }
}

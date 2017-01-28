node {
    stage("SCM"){
        echo "Build#${env.BUILD_ID}:Hello Stage SCM" 
		env
    }
}

node {
    stage("Build"){
        echo "Build#${env.BUILD_ID}:Hello Stage Build"
    }
}

node {
    stage("Test"){
        echo "Build#${env.BUILD_ID}:Hello Stage Test"
    }
}

node {
    stage("Deploy"){
        echo "Build#${env.BUILD_ID}:Hello Stage Deploy"
    }
}

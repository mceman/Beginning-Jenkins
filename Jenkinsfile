node {
    printMessage("Pipeline Start")

    stage("Fetch Source Code") {
        git "https://github.com/mceman/Beginning-Jenkins.git"
    }

    dir('Lesson5/ActivityA') {
        stage("Install Requirements") {
            sh 'apk add make'
            sh 'apk add python python-dev py-pip build-base'
            sh 'pip install virtualenv'
            sh 'make install'
        }

        stage("Run Tests") {
            sh 'make jenkins_test'
        }

        stage("Deploy") {
            if (env.BRANCH_NAME == "master") {
                printMessage("deploying master branch")
            } else {
                printMessage("no deployment specified for this branch")
            }
        }
    }

    printMessage("Pipeline End")
}

def printMessage(message) {
    echo "${message}"
}

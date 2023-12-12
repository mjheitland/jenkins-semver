pipeline {
    agent any

    environment {
        NEXT_VERSION = nextVersion()
    }

    stages {
        stage('Hello') {
            steps {
                echo "next version = ${NEXT_VERSION}"
            }
        }
    }
}
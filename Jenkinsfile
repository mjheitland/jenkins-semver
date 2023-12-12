pipeline {
    agent any

    environment {
        NEXT_VERSION = nextVersion()
    }

    stages {
        stage('Hello') {
            steps {
                sh '''#! /usr/bin/env bash
                    git config --local user.name github-release[bot]
                    git config --local user.email github-release-bot@mjheitland.com

                    version=${NEXT_VERSION}
                    major_version=$(cut -d'.' -f1 <<<"${version}")
                    minor_version=$(cut -d'.' -f2 <<<"${version}")

                    git push origin :${major_version} || true
                    git push origin :${major_version}.${minor_version} || true
                    git tag -d ${major_version} || true
                    git tag -d ${major_version}.${minor_version} || true
                    git tag -a ${major_version} -m "Release ${major_version}"
                    git tag -a ${major_version}.${minor_version} -m "Release ${major_version}.${minor_version}"
                    git push origin ${major_version}
                    git push origin ${major_version}.${minor_version}
                '''
            }
        }
    }
}
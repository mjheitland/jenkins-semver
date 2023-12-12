pipeline {
    agent any

    stages { 
        // stage('Checkout') {
        //     steps {
        //         // Delete the entire workspace
        //         deleteDir()

        //         git branch: 'main',
        //             credentialsId: 'GITHUB_USER',
        //             url: 'git@github.com:mjheitland/jenkins-semver.git'
        //     }
        // }

        stage('Tag') {
            environment {
                NEXT_VERSION = nextVersion()
            }

            steps {
                echo "next version = ${NEXT_VERSION}"

                sh '''#! /usr/bin/env bash
                    set -xeo pipefail
                    ls -al
                    git config --local user.name github-release[bot]
                    git config --local user.email github-release-bot@mjheitland.com
                    echo "Next git version (used as tag): ${NEXT_VERSION}"
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
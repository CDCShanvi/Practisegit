pipeline {
    agent any
    options {
        timeout(time: 20, unit: 'MINUTES') // Set the timeout to 20 minutes
    }
    tools {
        nodejs "node" // Assuming "node" is the name of your Node.js tool installation in Jenkins
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('GitClone') {
            steps {
                script {
                    def branchName = getBranchName()
                    echo "User Selected branch is in feature branch ${branchName}"
                    echo "Cloning Repository ${branchName}"
                    git credentialsId: '178479b6-2e4f-4d28-bc8c-050f6b7012bd', url: 'https://github.com/Curious-Ecosystem/Mentor-Mentees-Connect', branch: branchName
                }
            }
        }
        stage('Build') {
            steps {
                dir('Frontend-Assets/') {
                    echo 'Inside ' + pwd()
                    bat 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    dir("C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\React JS - Alpha\\Jenkins\\Scripts\\") {
                        bat 'test.sh'
                    }
                }
            }
        }
        stage('Deliver') {
            steps {
                script {
                    dir("C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\React JS - Alpha\\Jenkins\\Scripts\\") {
                        bat 'deliver.sh'
                    }
                }
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                script {
                    dir("C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\React JS - Alpha\\Jenkins\\Scripts\\") {
                        bat 'kill.sh'
                    }
                }
            }
        }
    }
}

def getBranchName() {
    def branchName = params.BranchName ?: env.BRANCH_NAME
    // Extract the last part of the branch name (after the last '/')
    def match = branchName =~ /.*\/(.*)/
    return match ? match[0][1] : branchName
}

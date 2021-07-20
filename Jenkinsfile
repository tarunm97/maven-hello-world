pipeline {

    agent none
    parameters{
     string(name: 'x', defaultValue: 'LW', description: 'dffddgfdgfd')
    }
    stages {
        stage('Build') {
             agent {
        node { label "test-docker" }
    }    
            steps {
                echo 'Build Stage'
                git branch: 'main', url: 'https://github.com/tarunm97/maven-hello-world.git'
                sh 'ls'
                sh 'cd my-app'
                stash includes: 'my-app/*', name: 'build'
            }
        }
        stage('Test') {
             agent {
        node { label "test-docker" }
    }    
            steps {
                unstash 'build'
                sh 'ls'
                echo 'Test Stage'
                sh 'cd my-app && mvn package'
                echo "Name is $Name"
            }

        }
        stage('Deploy') {
             agent {
        node { label "test-docker" }
    }    
            steps {
                echo 'Deploy Stage'
            }

        }
        stage('Monitor') {
            steps {
                echo 'Monitor Stage'
            }

        }
    }
}
    

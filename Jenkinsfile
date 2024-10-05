pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages {
        stage(src_code){
            steps{
                git 'https://github.com/Sudeepa8055/Spring_mySql_project.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('deploy') {
            steps {
                sh '''
                    echo "Stopping spring application processer"
                    sudo pkill -f target/my-shop-1.0.jar
                    # Start the Spring application
                    echo "Starting the Spring application..."
                    sudo java -jar target/my-shop-1.0.jar > /dev/null 2>&1 &
                '''
            }
        }
    }
}

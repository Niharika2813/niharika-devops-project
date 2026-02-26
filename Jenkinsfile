pipeline {
    agent any

    stages {

        stage('Deploy to Private EC2') {

            steps {

                sh '''
                scp -o StrictHostKeyChecking=no -i /var/lib/jenkins/demo-niharika-keypair.pem /var/lib/jenkins/workspace/niharika-pipeline/index.html ec2-user@10.0.2.137:/home/ec2-user/

                ssh -o StrictHostKeyChecking=no -i /var/lib/jenkins/demo-niharika-keypair.pem ec2-user@10.0.2.137 " "
                /usr/bin/docker stop myapp
                /usr/bin/docker rm myapp
                /usr/bin/docker run -d -p 80:80 --name myapp -v /home/ec2-user:/usr/share/nginx/html nginx

                "
                '''

            }

        }

    }

}


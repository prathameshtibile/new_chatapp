pipeline {
    agent any

    stages {
        stage('Git repo Cloning') {
            steps {
                git  'git clone https://github.com/prathameshtibile/CodeDeploy.git '
            }
        }

        stage('Build') {
            steps {

               sh ' rsync -avz -e 'ssh -i /var/lib/jenkins/backend.pem' /var/lib/jenkins/workspace/chatapp ec2-user@10.0.2.70:~
               #sh 'ssh -i /var/lib/jenkins/public_instance_key.pem ubuntu@10.0.1.10 "bash /home/ubuntu/chatapp/script/Before_inst.sh"'
               #sh 'ssh -i /var/lib/jenkins/public_instance_key.pem ubuntu@10.0.1.10 "bash /home/ubuntu/chatapp/script/move.sh"'

               }
        }
        stage('Deploy') {
            steps {
               sh 'ssh -i /var/lib/jenkins/backend.pem ec2-user@10.0.2.70 "bash /home/ec2-user/chatapp/"'

            }
        }
    }
}

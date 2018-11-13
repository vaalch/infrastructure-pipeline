properties([pipelineTriggers([githubPush()])])
node('linux') {
    git url: 'https://github.com/vaalch/infrastructure-pipeline.git', branch: 'master'
    stage('Test') {
        sh "env"
    }
}

stage ("GetInstances") {

    sh "aws ec2 describe-instances --region us-east-1"
}

stage ("CreateInstance") {
    aws ec2 run-instances --image-id ami-013be31976ca2c322 --count 1 --instance-type t2.micro --key-name KeyPair1.pem --security-group-ids sg-0b2bc601ae6e7e278 --subnet-id subnet-0184eaacf742833e1 --region us-east-1

}

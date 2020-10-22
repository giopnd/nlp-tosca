pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret')
    }
    stages {
        stage('Deploy resources') {
            environment {
                DEPLOY_FILE = '_definitions/steIgeneral__atc-nlp-demo_w1-wip1.tosca'
            }
            steps {
                sh 'unzip -o atc-nlp-demo_w1-wip1.csar'
                sh 'pip3 install boto3 ansible opera --user'
                sh 'mkdir -p /tmp && cp nodetypes/radon.nodes.legacy/AwsCreateRole/files/policy/policy.json /tmp/policy.json'
                sh 'PATH="$(python3 -m site --user-base)/bin:${PATH}" && opera deploy $DEPLOY_FILE'
            }
        }
    }
}

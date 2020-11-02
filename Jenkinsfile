pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret')
    }
    stages {
        stage('Deploy resources') {
            environment {
                DEPLOY_FILE = '_definitions/steIgeneral__viarota-nlp-pipeline_w1-wip1.tosca'
            }
            steps {
                sh 'unzip -o viarota-nlp-pipeline_w1-wip1.csar'
                sh 'python3 -m venv .venv && . .venv/bin/activate && pip install opera && yes Y | opera deploy --clean-state $DEPLOY_FILE'
                // sh 'python3 -m venv .venv && . .venv/bin/activate && pip install opera && opera undeploy'
            }
        }
    }
}

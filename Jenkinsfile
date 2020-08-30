pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: packer
    image: hashicorp/packer 
    command: 
    - bash
    tty: true
"""
    }
  }
  environment {
    CREDS = credentials('alhanouf_aws_creds')
    AWS_ACCESS_KEY_ID = "${CREDS_USR}"
    AWS_SECRET_ACCESS_KEY = "${CREDS_PSW}"
    OWNER = 'rho'
    PROJECT_NAME = 'rho-web-server'
    TOKEN=credentials('0c8899ba-7c49-4de5-859f-01d6f1584075')
  }
  stages {
      stage("build") {
          steps {
              container('packer') {
                  sh 'packer build packer.json'
              }
          }
      }
  }
}

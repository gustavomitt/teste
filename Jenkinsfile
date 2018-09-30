def label = "jenkins-pod-${UUID.randomUUID().toString()}"
podTemplate(label: label, yaml: """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: curl
    image: tutum/curl
    command: ['cat']
    tty: true
"""
  ) {
    node(label) {
        stage('Health') {
            container('curl') {
                git url: 'https://github.com/gustavomitt/teste.git'
                sh "cat Jenkinsfile"
                sh """
                #!/bin/bash
                echo "hello world"
                """
                sh "bash teste.sh"
            }
        }
    }
}


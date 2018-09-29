def label = "jenkins-pod-${UUID.randomUUID().toString()}"
podTemplate(label: label, yaml: """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: curl
    image: byrnedo/alpine-curl
    command: ['cat']
    tty: true
"""
pipeline {
  agent none
  stages {
    stage('teste') {
      container('curl') {
        steps {
          echo 'Oi!'
        }
      }
    }
  }
}

pipeline {
  agent {
    label 'skopeo'
  }
  stages {
    stage('Build') {
      steps {
        echo "Hello"
        sh " skopeo -v"
        sh "  skopeo copy docker://docker-registry.default.svc:5000/qa/service1 docker://docker-registry.default.svc:5000/prod/service1                --dest-tls-verify=false  --src-tls-verify=false    --dest-creds admin:peMQFvp95smL_vOrNar_VesyVBLrKvH03Dkx-Ajdao4 --src-creds=admin:peMQFvp95smL_vOrNar_VesyVBLrKvH03Dkx-Ajdao4 "
      }
    }
   
  }
}

#!groovy

def datas

node {

   stage('Read File') {
        echo "Reading File"
        git 'https://github.com/Tses/pipeline.git'
        echo "Checked Out"
        datas = readYaml file: 'promotes2.yaml'
    }
}

for (microservice in datas) {
  echo "service name :" + microservice.name
  echo "service version:" + microservice.version          
  deployService (microservice.name,microservice.version)
}

def deployService(serviceName,serviceVersion) {
  node {
    echo "calling build ${serviceName}"
    stage(serviceName) {
        sh " oc start-build ${serviceName}-pipeline -F -n jenkins1 --env=IMAGE_TAG=${serviceVersion}"
    }
     echo "called build ${serviceName}"
  }
}
  
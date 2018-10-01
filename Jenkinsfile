#!groovy


def datas

node {

   stage('Read File') {
       
        echo "Reading File"
        git 'https://github.com/Tses/pipeline.git'
        echo "Checked Out"

        datas = readYaml file: 'promotes.yaml'
        echo datas.service1.version
           
    }
}
if (datas.service1 != null) {
  echo "Service 1 Is not Null"
  deployService ("service1")
  
} else {
  echo "Service 1 Is Null"
}  
if (datas.service2 != null) {
  echo "Service 2 Is not Null"
  deployService ("service2")

} else {
  echo "Service 2  Is Null"
}          
if (datas.service3 != null) {
  echo "Service 3  Is not Null"
} else {
  echo "Service 3  Is Null"
}           
    


def deployService(serviceName) {
  node {
    
    echo "calling build ${serviceName}"
    stage(serviceName) {
        sh " oc start-build ${serviceName}-pipeline -F -n jenkins1 "
    }
     echo "called build ${serviceName}"
  }
}
  
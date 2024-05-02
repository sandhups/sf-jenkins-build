pipeline {
  agent {
    docker {
      image "python:3.8"
      args '--user 0:0'
    }
  }
  stages {
    stage('Run schemaChange') {
      steps {
        sh "pip install schemachange --upgrage"
        sh "schemachange -f migrations -a ${SF_ACCOUNT} -u ${SF_USER} -r ${SF_ROLE} -w ${SF_WAREHOUSE} -d ${SF_DATABASE} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
      }
    }
  }
}
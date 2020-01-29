pipeline {
  agent any
  stages {
    stage('Create kubernetes cluster') {
      steps {
        withAWS(region: 'us-west-2', credentials: '292152339671') {
          sh '''
						eksctl create cluster 						--name capstonecluster 						--version 1.14 						--nodegroup-name standard-workers 						--node-type t2.small 						--nodes 2 						--nodes-min 1 						--nodes-max 3 						--node-ami auto
					'''
        }

      }
    }

    stage('Create conf file cluster') {
      steps {
        withAWS(region: 'us-west-2', credentials: '292152339671') {
          sh '''
						aws eks --region us-west-2 update-kubeconfig --name capstonecluster
					'''
        }

      }
    }

  }
}

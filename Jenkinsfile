pipeline {
  agent {
    node {
      label 'Flask-RLM'
    }

  }
  stages {
    stage('Set up environment') {
      steps {
        sh '''
              npm install

              sed -i \'s|YOUR_DOMAIN_HERE|https://nimbus.datalogics.com|g\' config/settings.js

              sed -i \'s|moveToS3 : true|moveToS3 : false|g\' config/settings.js

              wget https://media-bucket-dl.s3.us-east-2.amazonaws.com/Archive.zip
              mv Archive.zip /opt/datalogics/public
              unzip -o /opt/datalogics/public/Archive.zip -d /opt/datalogics/public/

              cd tests/collections

              sed -i \'s|zapier|nimbus|g\' collections.sh
            '''
      }
    }

    stage('Run Unit Tests') {
      steps {
        sh 'npm test'
      }
    }

    stage('Run Integration Tests') {
      steps {
        sh '''
              node server.js >server_test_logs &
              cd tests/collections
              ./collections.sh
              echo 'Running Tests on BMP'
              newman run 'bmp-route.json' --insecure

              echo 'Running Tests on JPG'
              newman run 'jpg-route.json' --insecure

              echo 'Running Tests on GIF'
              newman run 'gif-route.json' --insecure

              echo 'Running Tests on PNG'
              newman run 'png-route.json' --insecure

              echo 'Running Tests on TIF'
              newman run 'tif-route.json' --insecure

              echo 'Running Tests on PDF'
              newman run 'pdf-route.json' --insecure

              echo 'Running Tests on HTML'
              newman run 'html-route.json' --insecure

              echo 'Running Tests on GET'
              newman run 'get-route.json' --insecure

              echo 'Running Tests on PDFA'
              newman run 'pdfa-route.json' --insecure

              echo 'Running Tests on merged-PDF'
              newman run 'merged-pdf-route.json' --insecure

              echo 'Running Tests on merged-PDF'
              newman run 'split-pdf-route.json' --insecure

              echo 'Running Tests on compressed-PDF'
              newman run 'compressed-pdf-route.json' --insecure

              echo 'Running Tests on zip'
              newman run 'zip-route.json' --insecure

              pkill node
            '''
      }
    }

  }
}

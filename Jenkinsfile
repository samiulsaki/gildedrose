node {
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git credentialsId: 'd5173568-ebba-4b5a-9956-57ac598685b9', url: 'https://github.com/samiulsaki/gildedrose.git'

   }
   stage('Build') {
      // Run the maven build
      sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn install'
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/gildedrose-*.jar'
   }
   stage('Javadoc') {
      junit 'target/javadoc'
      archive 'target/gildedrose-*.jar'
   }
}

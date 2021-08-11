node {
  try{
    stage 'checkout project'
    checkout scm

    stage 'check env'
    sh "mvn -v"
    sh "java -version"

    stage 'build'
    sh "mvn clean install -DskipTests"

   

    stage 'report'
    step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])

    stage 'Artifact'
    step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar', fingerprint: true])

  }catch(e){
    throw e;
  }
}

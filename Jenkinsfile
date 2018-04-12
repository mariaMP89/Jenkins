#!groovy

node {
   // ------------------------------------
   // -- ETAPA: Construccion Proyecto angularCLi
   // ------------------------------------
   stage 'Build'
   
   // -- Configura variables
   echo 'Configurando variables'
   def mvnHome = tool 'M3'
   env.PATH = "${mvnHome}/bin:${env.PATH}"
   echo "var mvnHome='${mvnHome}'"
   echo "var env.PATH='${env.PATH}'"
   
   // -- Descarga código desde SCM node-ang5
   echo 'Descargando estructura de SCM '
   sh 'rm -rf *'
   checkout scm
    // -- Descarga código desde SCM lqp-ang5
   echo 'Descargando lqp de SCM'
   sh 'rm -rf *'
   checkout scm
   
   // ------------------------------------
   // -- ETAPA: Compilar
   // ------------------------------------
   stage 'Compilar'
   
   // -- Configura variables
   echo 'Configurando variables'
   def mvnHome = tool 'M3'
   env.PATH = "${mvnHome}/bin:${env.PATH}"
   echo "var mvnHome='${mvnHome}'"
   echo "var env.PATH='${env.PATH}'"
   
   // -- Compilando
   echo 'Compilando aplicación'
   sh 'mvn clean compile'
   
   // ------------------------------------
   // -- ETAPA: Test
   // ------------------------------------
   stage 'Test'
   echo 'Ejecutando tests'
   try{
      sh 'mvn verify'
      step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
   }catch(err) {
      step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
      if (currentBuild.result == 'UNSTABLE')
         currentBuild.result = 'FAILURE'
      throw err
   }
      // ------------------------------------
   // -- ETAPA: Sonar
   // ------------------------------------
   stage 'SOnar'
   echo 'Ejecutando pruebas Sonar'
    
   // ------------------------------------
   // -- ETAPA: Empaquetado y versionado
   // ------------------------------------
   stage 'Empaquetar y versionado'
   echo 'Instala el paquete generado en el repositorio maven'
   sh 'mvn install -Dmaven.test.skip=true'
   
   // ------------------------------------
   // -- ETAPA: Nexus
   // ------------------------------------
   stage 'Subida Nexus'
   echo 'Subida a nexus delpaquete generado en Jenkins'
   step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar, **/target/*.war', fingerprint: true])
}

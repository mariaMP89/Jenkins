#!groovy

node {
   // ------------------------------------
   // -- ETAPA: Construccion Proyecto angularCLi
   // ------------------------------------
   stage 'Build'      
   // -- Configura variables

   echo 'Configurando variables'
  
           
   // -- Descarga código desde SCM node-ang5
   echo 'Descargando estructura de SCM '
   
    // -- Descarga código desde SCM lqp-ang5
    echo 'Descargando lqp de SCM'
   
   // ------------------------------------
   // -- ETAPA: Compilar
   // ------------------------------------
   stage 'Compilar'
   
   // -- Configura variables
   echo 'Configurando variables'
   
   
   // -- Compilando
   echo 'Compilando aplicación'
  
   
   // ------------------------------------
   // -- ETAPA: Test
   // ------------------------------------
   stage 'Test'
   echo 'Ejecutando tests'
   
      // ------------------------------------
   // -- ETAPA: Sonar
   // ------------------------------------
   stage 'Sonar'
   echo 'Ejecutando pruebas Sonar'
   
   // ------------------------------------
   // -- ETAPA: Empaquetado y versionado
   // ------------------------------------
   stage 'Empaquetar y versionado'
   echo 'Instala el paquete generado en el repositorio maven'
   
   
   // ------------------------------------
   // -- ETAPA: Nexus
   // ------------------------------------
   stage 'Subida Nexus'
   echo 'Subida a nexus delpaquete generado en Jenkins'
   
}

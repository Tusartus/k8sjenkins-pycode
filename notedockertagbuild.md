## If you want to prepend the build number with a "v" (e.g., "v1", "v2", "v3", etc.), you can simply modify your string concatenation:

stage('Push image') {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-cred') {
        app.push("v${env.BUILD_NUMBER}")
    }
}


And for the Trigger ManifestUpdate stage:    build jobs is set first in new item  + add triiger parametized      name: DoCKERTAG,   default: latest   ( here image)  


Then, in the script where you modify the deployment.yaml file, the sed command will replace based on the DOCKERTAG value:


sh "sed -i 's+22nit/flaskcicd.*+22nit/flaskcicd:${DOCKERTAG}+g' deployment.yaml"







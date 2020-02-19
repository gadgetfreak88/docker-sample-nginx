node {
   stage('SCM Checkout'){
    // Clone repo
   git credentialsId: '9f54c9ee-03e2-442f-9b07-6b8c3ea41846', 
   url: 'https://github.com/gadgetfreak88/docker-sample-nginx.git',
   branch: 'master' 
   }
   stage('Docker Build'){
    sh 'docker build -t nginx-test .'   
   }
   stage('Stop existing container'){
    sh 'docker container stop nginx-test && sleep 12'
   }
   stage('Docker run'){
    sh 'docker container run --rm -d -p 81:80 -l traefik.http.routers.nginx.rule=Host(\`nginx.docker.localhost\`)" --name nginx-test nginx-test:latest'
   }
}
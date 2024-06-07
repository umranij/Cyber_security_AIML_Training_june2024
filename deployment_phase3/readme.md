`
1. Get Completed application 
2. Using 12 factor design create Dockerfile 
3. Deploy image and containers on operational cluster 

`

16 cd .\deployment_phase3\
  17 git init
  18 git status
  19 git add .
  20 git status
  21 git commit -m "added for deployement"
  22 git remote add origin https://github.com/vishymails/cyber-deploy.git
  23 git push
  24 git push -u origin main
  25 git push -u origin master



  git clone https://github.com/vishymails/cyber-deploy.git
    5  ls
    6  cd cyber-deploy
    7  ls
    8  docker build -t cyber-deploy:1.0 .
    9  docker run -p 5000:5000 cyber-deploy:1.0
   10  docker run -p 5001:5000 cyber-deploy:1.0

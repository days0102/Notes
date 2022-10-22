<!--
 * @Author: Outsider
 * @Date: 2022-10-22 08:31:18
 * @LastEditors: Outsider
 * @LastEditTime: 2022-10-22 08:38:42
 * @Description: In User Settings Edit
 * @FilePath: \Notes\Docker\jenkin.md
-->
## start 
- docker run \                                                  
  --name jenkins \
  -it --rm \           
  -p 8080:8080 \
  -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home:z \
  --env="JENKINS_OPTS=--prefix=/jenkins" \
  -v deploy:/var/deploy:z \
  cst

n:lwz
pd:411...04
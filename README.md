# Kubernetes
Kubernetes related knowledge including CKAD prep material

VIM tips and tricks - https://www.dbi-services.com/blog/vim-tips-tricks-for-the-kubernetes-cka-exam/

1) show line#s  : set nu
2) copy and insert a block
    a) show line#s
    b) : 12,16y
    c) : 26gg
    d) p 
3) go to line# with particular word -  /word
4) search and replace - %s/nginx/web
5) using registers to copy and paste
     a) 11gg and "ayy - go to line 11 and yank to register a 
     b) 24gg and "byy - go to line 24 and yank to register b
     c) 29gg and "ap"bp - paste line 11 and line 24 in line 29
6) Using visual blocks
   i) shift a block 3 chars to the left
       a) 8gg and press 0 to go the beginning of line 8
       b) press cntrl+v to enter visual block
       c) press down arrow to select all the lines that need to be shifted
       d) press left arrow 3 times
   ii) shift a block 1 char to the right
       a) 8gg
       b) press cntrl+v to enter visual block
       c) press down arrow to select all the lines that need to be shifted
       d) press shift+i then space bar
       e) press ESC button twice
7) Very important - undo changes Press ESC + u | replay last action cntrl + r
8) Copy paste from kubernetes.io to yaml files - :set paste once paste is done :set nopaste to disable auto-indenting

Kubernetes commands 

1) Describe pod - Kubectl describe pods –namespace=kube-system | grep -C 10 labels:    k get events
2) Executing a command inside a container - K exec -it wordpress -- ls -l   | k exec pod-name -it -- /bin/sh
3) For connecting to a certain IP: wget --spider --timeout=1 10.244.1.2   or wget -O- www.google.com
4) To get IP and node name along with status - k get pod pod-name -o wide
5) Instead of deleting and recreating a pod - k replace -f pod.yaml -- force
6) To check configured env values at run time inside the container - k exec pod-name --env
7) To run an interactive terminal from a temporary pod inside the same cluster
    k get services - get IP of the service
    k run tmp –image=busybox -it – wget -o- IPAddressFromAbove:port
8) Labelling
    k get pods -l ‘team in (shiny,legacy)’, app=V1.1.24 - - show-labels
    k label pod pod-name region=au
9) rolling out a new version or changing image to another one
    k set image deployment my-deploy wordpress=wordpress:latest
    K rollout status deployment my-deploy
    K rollout history deployment my-deploy - - revision=2
    K rollout undo deployment my-deploy - -to-revision=1
    K describe pod pod-name | grep image
10) HPA - K autoscale deployment my-deploy –cpu-percent=70 –min=2, --max=8
11) cronjob ex: K create cronjob current-date –schedule=” * * * * *” - - image=wordpress - - /bin/sh -c ‘echo “Current Date: $(date)”’
12) expose deployment - k expose deployment my-deploy - - type=NodePort- -port=80 - -target-port=80 - -name=my-service

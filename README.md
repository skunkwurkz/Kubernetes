# Kubernetes
Kubernetes related knowledge including CKAD prep material

VIM tips and tricks - https://www.dbi-services.com/blog/vim-tips-tricks-for-the-kubernetes-cka-exam/

1) show line#s  : set nu
2) copy and insert a block
    a) show line#s
    b) : 12,16y
    c) : 26gg
    d) p
3) search or to to line# with particular word -  /word
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

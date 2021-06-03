## create a new repository on the command line
```git
echo "# lzb" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/liuzhaobo1999/lzb.git
git push -u origin master
```

## push an existing repository from the command line
```git
git remote add origin https://github.com/liuzhaobo1999/lzb.git
git branch -M master
git push -u origin master
```
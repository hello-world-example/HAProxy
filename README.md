# HAProxy 

空的模版项目

- cp -r HAProxy <NewProject>
- cd <NewProject>
- rm HAProxy.iml
- sed -i '' 's/HAProxy/<NewProject>/g' `grep HAProxy --include=\*.{md,html,xml} -rl .`
- git remote set-url origin https://github.com/hello-world-example/<NewProject>.git


# Flask_base

### 运行`base`项目

1. 在win中，创建虚拟环境
```cmd
python -m venv venv
```

2. 进入虚拟环境
```cmd
.\venv\Scripts\activate
```

2. 安装flask等依赖
```cmd
pip install -r requirements.txt
```

3. 启动！
```cmd
python app.py
```

___

### `Git`相关

https://blog.csdn.net/sculpta/article/details/104448310

1. check branch 

```git local bash
git branch
```

2. check all branch
```
git branch -a
```

3. create branch dev and choise
```
git checkout -b dev origin/dev
```

4. if you are developing login model, you can run the command blow:
```
git checkout dev
git checkout -b feature/login_module
git branch -v
git push origin feature/login_module:feature/login_module
git add <new files>
git commit -m "login module finished"
git push origin feature/login_module
```

5. Then you can submit PR in github!

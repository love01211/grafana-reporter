# 效果
![image](https://user-images.githubusercontent.com/31766073/119476250-76b57880-bd80-11eb-8edc-5dca1ea78e94.png)

# centos7编译
```
1.切换目录到$GOPATH/src/
git clone https://github.com/love01211/grafana-reporter.git
2.编译生成二进制文件在$GOPATH/bin/
go install -v grafana-reporter/cmd/grafana-reporter
```

# grafana-reporter
导出pdf后时间格式化为yyyy-MM-dd HH:MM:SS，替换latex打印pdf，title支持中文
# go编译后使用问题
## 问题1：error calling LaTeX preprocessing: "exec: \"xelatex\": executable file not found in $PATH". Latex preprocessing failed with output:
解决办法：yum install texlive-latex-bin texlive-xetex-bin texmaker（配置base和epel源）
`如果安装过程中遇到版本冲突，使用yum卸载冲突的版本（同时卸载依赖），然后再次执行上条命令`
## 问题2：error calling LaTeX preprocessing: "exit status 1". Latex preprocessing failed with output: This is XeTeX, Version 3.1415926-2.5-0.9999.3 (TeX Live 2013)
![report报错2](https://user-images.githubusercontent.com/31766073/118921392-ab819400-b96a-11eb-9349-2d44b9ab94e4.png)
解决办法
```
cp -r xecjk/* /usr/share/texlive/texmf-dist/tex/xelatex/xecjk/
cp euenc/* /usr/share/texlive/texmf-dist/tex/latex/euenc/
cp SIMKAI.ttf /usr/share/fonts/dejavu/
  
  执行命令重新加载：texhash
  上述文件在resources文件夹下
```

# 原作者地址
https://github.com/IzakMarais/reporter

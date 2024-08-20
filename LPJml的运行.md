# LPJml的运行
# 1. 查看命令帮助
```bash
lpjml -h
#     lpjml C Version 5.7.9 (Jul 16 2024) Help
#     ========================================
# 
# Dynamic global vegetation model with managed land
# 
# Usage: lpjml [-h] [-l] [-v] [-vv] [-param] [-pp cmd] [-fpe]
#        [-couple host[:port]] [-wait time]
#        [-outpath dir] [-inpath dir] [-restartpath dir]
#        [[-Dmacro[=value]] [-Idir] ...] filename
# 
# Arguments:
# -h                  print this help text
# -l                  print license file
# -v                  print version, compiler and compile flags
# -vv                 verbosely print the actual values during reading of the
#                     configuration files
# -param              print LPJmL parameter
# -pp cmd             set preprocessor program. Default is 'cpp'
# -fpe                enable floating point exceptions
# -couple host[:port] set host and port where coupled model is running
# -wait time          time to wait for connection to coupled/IMAGE model (sec)
# -outpath dir        directory appended to output filenames
# -inpath dir         directory appended to input filenames
# -restartpath dir    directory appended to restart filename
# -Dmacro[=value]     define macro for preprocessor of configuration file 宏，使用-D宏名
# -Idir               directory to search for include files
# filename            configuration filename 配置文件必须有
```
# 2. 预热期的运行命令：

```bash
lpjml lpj.js
```
在编译的编译时有mpich，可以使用并行执行
```bash
mpirun --allow-run-as-root -np 3 lpjml lpj.js #3为并行数量，根据自己设备情况定。
nohup mpirun --allow-run-as-root -np 3 lpjml lpj.js > lpjml20240809.log 2>&1 & #在后台运行，命令输出内容存储到lpjml20240809.log文件件中
```

# 3. 正式开始模拟
```bash
lpjml -DFROM_RESTART lpj.js
lpjml -DFROM_RESTART -outpath /a_path/b_path/c_path/ lpj.js #如果配置文件中写输输出文件是相对路径，则推荐写这个参数或配置成环境变量LPJOUTPATH
```

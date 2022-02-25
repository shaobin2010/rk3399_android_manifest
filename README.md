步骤
1）创建一个空目录来保存您的工作文件：

1
2
$mkdir -p WORKING_DIRECTORY
$cd WORKING_DIRECTORY
2）首先运行repo init下载清单存储库：

android 10.0:

1
$repo init -u https://github.com/khadas/android_manifest.git -b khadas-edge-Qt
android 9.0:

1
$repo init -u https://github.com/khadas/android_manifest.git -b khadas-edge-pie
android 7.1:

1
$repo init -u https://github.com/khadas/android_manifest.git -b khadas-edge-nougat
3）运行repo-sync下拉Android源代码：

1
$repo sync -j4
初始同步操作可能需要很长时间才能完成。
提示：如果命令中途失败，您可能需要重复运行上面的命令。或者您可以尝试使用此脚本：

提示
如果命令中途失败，您可能需要重复运行上面的命令。或者您可以尝试使用此脚本

1
2
3
4
5
6
#!/bin/bash
repo sync -j4
while [ $? = 1 ]; do
    echo "Sync failed, repeat again:"
    repo sync -j4
done
如果需要，请按ctrl-\退出。

4）建立开发分支：

1
$ repo start <BRANCH_NAME> --all

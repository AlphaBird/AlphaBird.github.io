-- 

记录一下自己在Mac下安装sklearn时遇到的问题和解决的方法，供大家参考。

注：MacBook Pro，系统是OS X EI Captain，Version 10.11.3


一、遇到的问题

安装scikit-learn：

```
pip install scikit-learn
```

（Mac OS自带的Python，用brew工具装了pip）

安装完毕，打开Python，import sklearn，出错，主要错误如下：


```
from sklearn import datasets
```
错误提示：ValueError: numpy.dtype has the wrong size, try recompiling

```
from sklearn import svm
```
错误提示：ImportError: cannot import name __check_build

用pip更新了sklearn还是不行
pip update sklearn


二、解决方法

1、sklearn对numpy包有依赖，因此索性更新了numpy、scipy：
```
pip update numpy
pip update scipy
```

2、然后卸载sklearn：
```
pip uninstall scikit-learn
```

3、重新安装sklearn：
```
pip install scikit-learn --user python
```

再次启动Python，再次import sklearn，不报错，成功。

注意如果第3步用pip install scikit-learn，就是不加`--user python`，会出错，出错信息如下：

![](/source/images/oserror.png)

原因是 OS X El Capitan系统引入了System Integrity Protection，需要加`--user python`.

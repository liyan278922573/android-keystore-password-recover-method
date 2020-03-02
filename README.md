## 找回Android keystore密码方法收集

有效程度按星级⭐️标记📌

### Gradle缓存中查找

#### 方法01 ⭐️⭐️⭐️

定位到项目的以下文件（如果有）

```
.gradle\2.4\taskArtifacts\taskArtifacts.bin
.gradle/3.5/taskHistory/taskHistory.bin
.gradle/5.1.1/executionHistory/executionHistory.bin
.gradle/caches/5.1.1/executionHistory/executionHistory.bin
```

使用Android Studio打开文件📃

尝试搜索🔍关键字 `storePassword`

#### 方法02（推荐） ⭐️⭐️⭐️⭐️

定位到项目以下文件（如果有）

```
app\build\intermediates\signing_config\release\out\signing-config.json
```

尝试搜索🔍关键字 `mStorePassword` 和 `mKeyPassword`

### Android Studio缓存中查找 ⭐️⭐️

定位到以下目录(macOS)

```
〜/Library/Logs -> AndroidStudio -> idea.log.1（或任何旧的日志号）
```

尝试搜索🔍关键字 `keystore`

### 使用工具暴力破解

推荐使用 `android-keystore-password-recover`  (本仓库可下载jar包和源代码)

[官网介绍](https://maxcamillo.github.io/android-keystore-password-recover/)

#### 使用说明

##### 1. 简单破解 ⭐️⭐️

```
java -jar android-keystore-password-recover.jar -m 1 -k {keystore路径} -start {提示字符}
```

##### 2. 字典破解 ⭐️⭐️⭐️

```
java -jar android-keystore-password-recover.jar -m 2 -k {keystore路径} -d "wordlist.txt"
```

##### 3. 智能词表破解 (推荐) ⭐️⭐️⭐️⭐️

```
java -jar android-keystore-password-recover.jar -m 3 -k {keystore路径} -d "wordlist.txt"
```

### 参考文档

- [how-to-handle-a-lost-keystore-password-in-android](https://stackoverflow.com/questions/6089813/how-to-handle-a-lost-keystore-password-in-android)
- [android发布新版忘记keystore(jks)密码终极解决方案](https://www.cnblogs.com/yyoba/p/9318105.htm)

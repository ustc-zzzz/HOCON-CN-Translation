# HOCON-CN-Translation

Here is the GitHub repository of the unofficial Simplified Chinese translation of [HOCON.md in `lightbend/config`](https://github.com/lightbend/config/blob/master/HOCON.md), mainly maintained by [@ustc-zzzz](https://github.com/ustc-zzzz) and [@3TUSK](https://github.com/3TUSK). The entire translation is located in [HOCON.md](HOCON.md) of the repository.

这里是 [`lightbend/config` 项目的 HOCON.md](https://github.com/lightbend/config/blob/master/HOCON.md) 的非官方简体中文翻译的 GitHub 仓库，由 [@ustc-zzzz](https://github.com/ustc-zzzz) 和 [@3TUSK](https://github.com/3TUSK) 主要负责维护。整个翻译位于仓库的 [HOCON.md](HOCON.md) 中。

## 协议

原文和本翻译均使用 [Apache 2.0 协议](LICENSE)发布。

## 翻译约定

翻译格式严格按照[中文文案排版指北（简体中文版）](https://github.com/mzlogin/chinese-copywriting-guidelines)进行，但有以下几个例外和补充约定：

* 链接之间不加空格
* 简体中文使用全角西式引号，而非直角引号
* 遇到斜体文本，翻译时将格式转换成粗体，因为中文排版本身不适合斜体

此外，在英译汉翻译本身方面，还有以下额外约定：

* 遇到某个英文链接时，如有对应中文链接（如对应翻译等），翻译时选择对应中文链接
* 对于特殊概念，可以在后面附上全小写字母组成的英文原文，并用括号括起来
* 特定术语的翻译首先以 JSON 官方规范为准，其次以已经出现的翻译为准
* 代表某个特定字符或字符串的英文原文，两边的引号使用原半角形式
* 代码段里的英文保持原样不翻译

## 翻译状态

- [HOCON（人性化配置对象表示法，Human-Optimized Config Object Notation）](HOCON.md#hocon%E4%BA%BA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE%E5%AF%B9%E8%B1%A1%E8%A1%A8%E7%A4%BA%E6%B3%95human-optimized-config-object-notation)（3TUSK，ustc-zzzz）
  - [目标/背景](HOCON.md#%E7%9B%AE%E6%A0%87%E8%83%8C%E6%99%AF)（ustc-zzzz）
  - [定义](HOCON.md#%E5%AE%9A%E4%B9%89)（ustc-zzzz）
  - [语法](HOCON.md#%E8%AF%AD%E6%B3%95)（3TUSK，ustc-zzzz）
    - [和 JSON 一样的地方](HOCON.md#%E5%92%8C-json-%E4%B8%80%E6%A0%B7%E7%9A%84%E5%9C%B0%E6%96%B9)（ustc-zzzz）
    - [注释](HOCON.md#%E6%B3%A8%E9%87%8A)（ustc-zzzz）
    - [对根结构更宽松的要求](HOCON.md#%E5%AF%B9%E6%A0%B9%E7%BB%93%E6%9E%84%E6%9B%B4%E5%AE%BD%E6%9D%BE%E7%9A%84%E8%A6%81%E6%B1%82)（ustc-zzzz）
    - [键值分隔符](HOCON.md#%E9%94%AE%E5%80%BC%E5%88%86%E9%9A%94%E7%AC%A6)（ustc-zzzz）
    - [逗号](HOCON.md#%E9%80%97%E5%8F%B7)（ustc-zzzz）
    - [空白](HOCON.md#%E7%A9%BA%E7%99%BD)（3TUSK）
    - [重复键与对象合并](HOCON.md#%E9%87%8D%E5%A4%8D%E9%94%AE%E4%B8%8E%E5%AF%B9%E8%B1%A1%E5%90%88%E5%B9%B6)（3TUSK）
    - [不加引号的字符串](HOCON.md#%E4%B8%8D%E5%8A%A0%E5%BC%95%E5%8F%B7%E7%9A%84%E5%AD%97%E7%AC%A6%E4%B8%B2)（ustc-zzzz）
    - [多行字符串](HOCON.md#%E5%A4%9A%E8%A1%8C%E5%AD%97%E7%AC%A6%E4%B8%B2)（ustc-zzzz）
    - [值连结](HOCON.md#%E5%80%BC%E8%BF%9E%E7%BB%93)（ustc-zzzz）
      - [字符串值连结](HOCON.md#%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%80%BC%E8%BF%9E%E7%BB%93)（ustc-zzzz）
      - [数组值连结和对象值连结](HOCON.md#%E6%95%B0%E7%BB%84%E5%80%BC%E8%BF%9E%E7%BB%93%E5%92%8C%E5%AF%B9%E8%B1%A1%E5%80%BC%E8%BF%9E%E7%BB%93)（ustc-zzzz）
      - [注意：引用之间含有空白的值连结](HOCON.md#%E6%B3%A8%E6%84%8F%E5%BC%95%E7%94%A8%E4%B9%8B%E9%97%B4%E5%90%AB%E6%9C%89%E7%A9%BA%E7%99%BD%E7%9A%84%E5%80%BC%E8%BF%9E%E7%BB%93)（ustc-zzzz）
      - [注意：不含有逗号或换行符的数组](HOCON.md#%E6%B3%A8%E6%84%8F%E4%B8%8D%E5%90%AB%E6%9C%89%E9%80%97%E5%8F%B7%E6%88%96%E6%8D%A2%E8%A1%8C%E7%AC%A6%E7%9A%84%E6%95%B0%E7%BB%84)（ustc-zzzz）
    - [路径表达式](HOCON.md#%E8%B7%AF%E5%BE%84%E8%A1%A8%E8%BE%BE%E5%BC%8F)（ustc-zzzz）
    - [作为键的路径表达式](HOCON.md#%E4%BD%9C%E4%B8%BA%E9%94%AE%E7%9A%84%E8%B7%AF%E5%BE%84%E8%A1%A8%E8%BE%BE%E5%BC%8F)（ustc-zzzz）
    - [引用](HOCON.md#%E5%BC%95%E7%94%A8)（3TUSK，ustc-zzzz）
      - [自引用](HOCON.md#%E8%87%AA%E5%BC%95%E7%94%A8)（ustc-zzzz）
      - [键值分隔符 `+=`](HOCON.md#%E9%94%AE%E5%80%BC%E5%88%86%E9%9A%94%E7%AC%A6-)（3TUSK）
      - [自引用举例](HOCON.md#%E8%87%AA%E5%BC%95%E7%94%A8%E4%B8%BE%E4%BE%8B)（3TUSK）
    - [跨文件引用](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8)（ustc-zzzz）
      - [跨文件引用语法](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E6%B3%95)（ustc-zzzz）
      - [跨文件引用语义：合并](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E4%B9%89%E5%90%88%E5%B9%B6)（ustc-zzzz）
      - [跨文件引用语义：引用](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E4%B9%89%E5%BC%95%E7%94%A8)（ustc-zzzz）
      - [跨文件引用语义：不存在的文件和强制要求的文件](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E4%B9%89%E4%B8%8D%E5%AD%98%E5%9C%A8%E7%9A%84%E6%96%87%E4%BB%B6%E5%92%8C%E5%BC%BA%E5%88%B6%E8%A6%81%E6%B1%82%E7%9A%84%E6%96%87%E4%BB%B6)（ustc-zzzz）
      - [跨文件引用语义：文件类型及格式](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E4%B9%89%E6%96%87%E4%BB%B6%E7%B1%BB%E5%9E%8B%E5%8F%8A%E6%A0%BC%E5%BC%8F)（ustc-zzzz）
      - [跨文件引用语义：资源定位](HOCON.md#%E8%B7%A8%E6%96%87%E4%BB%B6%E5%BC%95%E7%94%A8%E8%AF%AD%E4%B9%89%E8%B5%84%E6%BA%90%E5%AE%9A%E4%BD%8D)（ustc-zzzz）
    - [数字索引对象到数组的转换](HOCON.md#%E6%95%B0%E5%AD%97%E7%B4%A2%E5%BC%95%E5%AF%B9%E8%B1%A1%E5%88%B0%E6%95%B0%E7%BB%84%E7%9A%84%E8%BD%AC%E6%8D%A2)（ustc-zzzz）
  - [MIME 类型](HOCON.md#mime-%E7%B1%BB%E5%9E%8B)（ustc-zzzz）
  - [对于 API 的建议](HOCON.md#%E5%AF%B9%E4%BA%8E-api-%E7%9A%84%E5%BB%BA%E8%AE%AE)（3TUSK，ustc-zzzz）
    - [自动类型转换](HOCON.md#%E8%87%AA%E5%8A%A8%E7%B1%BB%E5%9E%8B%E8%BD%AC%E6%8D%A2)（ustc-zzzz）
    - [单位格式](HOCON.md#%E5%8D%95%E4%BD%8D%E6%A0%BC%E5%BC%8F)（3TUSK）
    - [时间单位](HOCON.md#%E6%97%B6%E9%97%B4%E5%8D%95%E4%BD%8D)（3TUSK）
    - [日期单位](HOCON.md#%E6%97%A5%E6%9C%9F%E5%8D%95%E4%BD%8D)（3TUSK）
    - [字节单位描述的尺寸](HOCON.md#%E5%AD%97%E8%8A%82%E5%8D%95%E4%BD%8D%E6%8F%8F%E8%BF%B0%E7%9A%84%E5%B0%BA%E5%AF%B8)（3TUSK）
    - [配置对象合并与文件合并](HOCON.md#%E9%85%8D%E7%BD%AE%E5%AF%B9%E8%B1%A1%E5%90%88%E5%B9%B6%E4%B8%8E%E6%96%87%E4%BB%B6%E5%90%88%E5%B9%B6)（3TUSK）
    - [与 properties 文件之间的映射](HOCON.md#%E4%B8%8E-properties-%E6%96%87%E4%BB%B6%E4%B9%8B%E9%97%B4%E7%9A%84%E6%98%A0%E5%B0%84)（3TUSK）
    - [常规的 JVM 应用配置文件](HOCON.md#%E5%B8%B8%E8%A7%84%E7%9A%84-jvm-%E5%BA%94%E7%94%A8%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)（3TUSK）
    - [常规的系统属性覆盖](HOCON.md#%E5%B8%B8%E8%A7%84%E7%9A%84%E7%B3%BB%E7%BB%9F%E5%B1%9E%E6%80%A7%E8%A6%86%E7%9B%96)（3TUSK）
    - [环境变量用作引用解析的备选项](HOCON.md#%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E7%94%A8%E4%BD%9C%E5%BC%95%E7%94%A8%E8%A7%A3%E6%9E%90%E7%9A%84%E5%A4%87%E9%80%89%E9%A1%B9)（3TUSK）
    - [连字符还是小写驼峰？](HOCON.md#%E8%BF%9E%E5%AD%97%E7%AC%A6%E8%BF%98%E6%98%AF%E5%B0%8F%E5%86%99%E9%A9%BC%E5%B3%B0)（3TUSK）
  - [注意：和 Java 语言的 properties 文件的相似性](HOCON.md#%E6%B3%A8%E6%84%8F%E5%92%8C-java-%E8%AF%AD%E8%A8%80%E7%9A%84-properties-%E6%96%87%E4%BB%B6%E7%9A%84%E7%9B%B8%E4%BC%BC%E6%80%A7)（ustc-zzzz）
  - [注意：Windows 平台以及大小写敏感的环境变量](HOCON.md#%E6%B3%A8%E6%84%8Fwindows-%E5%B9%B3%E5%8F%B0%E4%BB%A5%E5%8F%8A%E5%A4%A7%E5%B0%8F%E5%86%99%E6%95%8F%E6%84%9F%E7%9A%84%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F)（ustc-zzzz）

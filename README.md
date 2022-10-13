# Android-Develop-exp
对于Gradle 7+版本中的不安全HTTP连接，我们需要指定布尔allowInsecureProtocol作为MavenArtifactRepository闭包的true。
maven {
    allowInsecureProtocol = true
    ...      
}

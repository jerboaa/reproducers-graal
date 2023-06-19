# Steps to reproduce
```
mvn clean package
```

## Fails with:

```
[INFO] -------------------------------------------------------------
[ERROR] COMPILATION ERROR : 
[INFO] -------------------------------------------------------------
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[24,36] cannot access com.oracle.svm.core.annotate.Substitute
  bad class file: /home/sgehwolf/.m2/repository/org/graalvm/sdk/graal-sdk/23.0.0/graal-sdk-23.0.0.jar(/com/oracle/svm/core/annotate/Substitute.class)
    class file has wrong version 61.0, should be 55.0
    Please remove or make sure it appears in the correct subdirectory of the classpath.
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[25,36] cannot access com.oracle.svm.core.annotate.TargetClass
  bad class file: /home/sgehwolf/.m2/repository/org/graalvm/sdk/graal-sdk/23.0.0/graal-sdk-23.0.0.jar(/com/oracle/svm/core/annotate/TargetClass.class)
    class file has wrong version 61.0, should be 55.0
    Please remove or make sure it appears in the correct subdirectory of the classpath.
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[30,2] cannot find symbol
  symbol: class TargetClass
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[34,6] cannot find symbol
  symbol:   class Substitute
  location: class version.TargetSub
[INFO] 4 errors 
[INFO] -------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.847 s
[INFO] Finished at: 2023-06-19T15:34:13+02:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.8.0:compile (default-compile) on project version: Compilation failure: Compilation failure: 
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[24,36] cannot access com.oracle.svm.core.annotate.Substitute
[ERROR]   bad class file: /home/sgehwolf/.m2/repository/org/graalvm/sdk/graal-sdk/23.0.0/graal-sdk-23.0.0.jar(/com/oracle/svm/core/annotate/Substitute.class)
[ERROR]     class file has wrong version 61.0, should be 55.0
[ERROR]     Please remove or make sure it appears in the correct subdirectory of the classpath.
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[25,36] cannot access com.oracle.svm.core.annotate.TargetClass
[ERROR]   bad class file: /home/sgehwolf/.m2/repository/org/graalvm/sdk/graal-sdk/23.0.0/graal-sdk-23.0.0.jar(/com/oracle/svm/core/annotate/TargetClass.class)
[ERROR]     class file has wrong version 61.0, should be 55.0
[ERROR]     Please remove or make sure it appears in the correct subdirectory of the classpath.
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[30,2] cannot find symbol
[ERROR]   symbol: class TargetClass
[ERROR] /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/src/main/java/version/TargetSub.java:[34,6] cannot find symbol
[ERROR]   symbol:   class Substitute
[ERROR]   location: class version.TargetSub
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
```

# Passes with Graal SDK 22.3.x

if the `graal-sdk` dependency version is being changed to `22.3.0` it starts to work.`
```
mvn clean package
[...]
[INFO] Building jar: /home/sgehwolf/Documents/mandrel/bugs/upstream-graal/reproducers-graal/graal-23-jdk11-compliance-repro/target/version.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.180 s
[INFO] Finished at: 2023-06-19T15:39:36+02:00
[INFO] ------------------------------------------------------------------------
```

### Try-catch与Try-with-resource

推荐在需要使用手动关闭的资源是使用try-with-resource。因为不需要你自己使用finally去手动调用它的close（）方法。他们都实现了AutoCloseAble接口，下面可以看到，第一段代码是.java文件，第二段是.class文件，只不过是被Idea反编译成了更容易看的代码。可以你觉得单个try-catch还可以，但是当你有多个资源需要循环嵌套try-catch的时候，try-with-resouce的优雅性就体现出来了。

```java
public String tyrWithResource(String filePath) throws IOException {
        try(BufferedReader bis = new BufferedReader(new FileReader(filePath))) {
            return bis.readLine();
        }catch (Exception e){
            return e.getMessage();
        }
    }
```

```java
public String tyrWithResource(String filePath) throws IOException {
        try {
            BufferedReader bis = new BufferedReader(new FileReader(filePath));

            String var3;
            try {
                var3 = bis.readLine();
            } catch (Throwable var6) {
                try {
                    bis.close();
                } catch (Throwable var5) {
                    var6.addSuppressed(var5);
                }

                throw var6;
            }

            bis.close();
            return var3;
        } catch (Exception var7) {
            Exception e = var7;
            return e.getMessage();
        }
    }
```

可以看到Java编译器在编译时会在字节码层面去优化我们的代码，自动帮我们去调用close方法。这样省去了我们自己去管理资源，提高了代码的简洁性和可读性。

#### 引用《EffectiveJava 》第三版
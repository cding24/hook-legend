Legend是一个Android的免root hook框架，主要原理：通过构造新旧方法对应的虚拟机的数据结构，然后将替换数据信息写到内存中。
dalvikOriginMethod的属性clazz、insns、registersSize、insSize、accessFlags等几个重新赋值为hookmethod的对应的数据信息
然后dalvikOriginMethod.nativeFunc重新赋值为dalvikOriginMethod的数据结构信息写入的内存地址memoryAddress

HookManager.getDefault().callSuper(thiz, intent)；调用原来的方法
两种使用方式：
      1. annotation方式
      @Hook("android.app.Activity::startActivity@android.content.Intent#参数2")
      HookManager.getDefault().applyHooks(xxxx.class);

     2. java代码方式
      HookManager.getDefault().hookMethod(originMethod, hookMethod);

支持4.2----6.0, 但是7.0不支持

# Android

## 基类

在创建扩展前，你需要先了解 SDK 相关的基类。

### LGOModule

LGOModule 是 API 的入口类，所有的请求都会直接调用 LGOModule 中的 build 方法。 你需要重写 build 方法，并返回一个 LGORequestable 实例。

### LGORequest

LGORequest 是请求类，任何请求都会被转换为 LGORequest 以承载相关的请求参数。

### LGORequestable

LGORequestable 是执行请求的实例，所有的请求最终执行者都是 LGORequestable。
你需要重写 request 方法，同步或异步地返回 LGOResponse 实例。

### LGOResponse

LGOResponse 是结果类，LGOResponse 会被转换为 JSON 数据并返回至 WebView。

## 编写扩展

### 创建 LGOModule 扩展类

创建一个新类 LGOTest.java 并继承 LGOModule。

```java
import com.opensource.legosdk.core.LGOModule;

public class LGOTest extends LGOModule {
}
```

### 创建 LGORequest 类

按照请求参数，创建 LGORequest 类。

```java
import com.opensource.legosdk.core.LGORequest;
import com.opensource.legosdk.core.LGORequestContext;

class LGOTestRequest extends LGORequest {

    String name;

    public LGOTestRequest(LGORequestContext context) {
        super(context);
    }

}
```

### 创建 LGOResponse 类

```java
import com.opensource.legosdk.core.LGOResponse;

class LGOTestResponse extends LGOResponse {

    String text;

    @NotNull
    @Override
    public HashMap<String, Object> resData() {
        HashMap<String, Object> data = super.resData();
        if (text != null) {
            data.put("text", text);
        }
        return data;
    }

}
```

### 创建 LGORequestable 类

一个实例 LGORequestable 代表一次请求，我们创建 LGOTestOperation 类并继承 LGORequestable，重写 requestSynchronize 方法以处理请求。

```java
class LGOTestOperation extends LGORequestable {

    LGOTestRequest request;

    @NotNull
    @Override
    public LGOResponse requestSynchronize() {
        LGOTestResponse response = new LGOTestResponse();
        response.text = "Hello, " + request.name + ".";
        return response;
    }
    
}
```

### 接收、分发请求

在第一步创建的 LGOTest 类中，重写 buildWithJSONObject 方法，以接收来自 Web 的请求，并返回 LGOTestOperation 实例。

```java
public class LGOTest extends LGOModule {

    @Nullable
    @Override
    public LGORequestable buildWithJSONObject(JSONObject obj, LGORequestContext context) {
        LGOTestRequest request = new LGOTestRequest(context);
        try {
            request.name = obj.getString("name");
        } catch (Exception e) {
            return LGORequestable.Companion.reject("UED.Test", -1, "invalid name.");
        }
        LGOTestOperation operation = new LGOTestOperation();
        operation.request = request;
        return operation;
    }

}
```

### 添加 meta-data 至 manifest.xml

最后，在 manifest.xml application 一节中，添加对应的 meta-data 信息即可。

其中 name 必须是 LGOModule. 开头，紧接着 API 标识。value 填入该类的完整标识符（包名 + 类名）。

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest ...>

    <application ...>
        
        <meta-data android:name="LGOModule.UED.Test" android:value="com.opensource.demo.LGOTest" />

    </application>

</manifest>
```
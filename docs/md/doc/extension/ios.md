# iOS

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

New file -> 创建一个 NSObject 类，并继承 LGOModule。

```objectivec
//
//  LGOTest.h

#import <LEGO-SDK/LGOProtocols.h>

@interface LGOTest : LGOModule

@end
```

```objectivec
//
//  LGOTest.m

#import "LGOTest.h"

@implementation LGOTest

+ (void)load {
    [[LGOCore modules] addModuleWithName:@"UED.Test" instance:[LGOTest new]];
}

@end
```

### 创建 LGORequest 类

按照请求参数信息，创建 Request 类。

```objectivec
//
//  LGOTest.m

#import "LGOTest.h"

@interface LGOTestRequest: LGORequest

@property (nonatomic, copy) NSString *name;

@end

@implementation LGOTestRequest

@end
```

### 创建 LGOResponse 类

按照返回值信息，创建 Response 类。

```objectivec
//
//  LGOTest.m

#import "LGOTest.h"

@interface LGOTestResponse : LGOResponse

@property (nonatomic, copy) NSString *text;

@end

@implementation LGOTestResponse

- (NSDictionary *)resData {
    return @{
             @"text": self.text != nil ? self.text : [NSNull null]
             };
}

@end

```

### 创建 LGORequestable 类

一个实例 LGORequestable 代表一次请求，我们创建 LGOTestOperation 类并继承 LGORequestable，重写 requestSynchronize 方法以处理请求。

```objectivec
@interface LGOTestOperation : LGORequestable

@property (nonatomic, strong) LGOTestRequest *request;

@end

@implementation LGOTestOperation

- (LGOResponse *)requestSynchronize {
    LGOTestResponse *response = [[LGOTestResponse alloc] init];
    response.text = [NSString stringWithFormat:@"Hello, %@.", self.request.name];
    return [response accept:nil];
}

@end
```

### 处理请求

在 LGOTest 类中，重写 ```buildWithDictionary``` 方法用于接收请求，并返回 LGORequestable。

```objectivec
@implementation LGOTest

- (LGORequestable *)buildWithDictionary:(NSDictionary *)dictionary context:(LGORequestContext *)context {
    LGOTestRequest *reqeust = [[LGOTestRequest alloc] init];
    reqeust.name = [dictionary[@"name"] isKindOfClass:[NSString class]] ? dictionary[@"name"] : nil;
    if (reqeust.name == nil) {
        return [LGORequestable rejectWithDomain:@"Test" code:-1 reason:@"invalid name."];
    }
    LGOTestOperation *operation = [[LGOTestOperation alloc] init];
    operation.request = reqeust;
    return operation;
}

@end
```
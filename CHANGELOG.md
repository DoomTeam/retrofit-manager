# Change Log

## Version 1.4.2

*2018-11-08*

* 优化：通过 `LMRxJava2CallAdapter` 适配(adapt)得到的 `Observable` 对象默认订阅在(`subscribeOn`)在 IO 线程上

## Version 1.4.1

*2018-10-08*

* 完善：在缓存拦截器中直接向服务器发起请求时，如果请求结果不成功（`networkResponse.isSuccessful()` 为 `false`）则直接返回 `networkResponse` 对象

## Version 1.4

*2018-09-30*

* 升级 gradle wrapper 版本到 4.6，AGP 版本到 3.2.0
* 升级 Retrofit 到 2.4.0，OkHttp 到 3.11.0，RxJava 到 2.2.2，RxAndroid 到 2.1.0
* 升级 Android 编译版本和目标版本到 28
* 修改缓存失效后从接口重新请求一次新数据的实现方式，因为 okhttp 升级到 3.11.0 之后之前的实现方式有问题
* 新增通过 RxJava 请求接口对缓存逻辑的支持

## Version 1.3

Sorry, 1.3 版本不小心搞丢了。

## Version 1.2

*2017-12-21*

* 新增 `onCanceled()` 回调方法，在请求被取消的情况下进行回调，在这种情况下不会在回调其他任意方法
* 修正在接口没有返回的情况下，`ApiStatusInterceptor#intercep` 没有被调用的问题
* `BaseResp` 增加 `msgCode` 和 `cacheTime` 两个字段
* 新增 `onError(Call, BaseResp)` 回调方法，可以获取到新增字段，之前的错误回调暂时保留，后面会废弃
* `onIntercepted` 回调方法的第二个参数由泛型改为 `BaseResp`
* `ApiStatusInterceptor#intercept` 方法的参数改为 `BaseResp`
* 新增错误类型定义类 `ErrorStatus` ，包含 `FAILURE` （失败）和 `NETWORK_UNAVAILABLE` （没有网络）

## Version 1.1

*2017-12-08*

* `RetrofitManager` 新增 `getOkHttpClient()` 方法，使 OkHttpClient 对象可以复用
* 修复：在 `RetrofitProvider` 中 `provideOkHttpConfig()` 返回 null 时，没有设置默认超时时间（30秒）的问题
* 给 `PagedBean` 中 `pageResult` 设置序列化别名 pageInfo ，以适配老接口中分页参数字段名为 pageInfo 的情况

## Version 1.0

*2017-11-21*

* **完成对 RxJava2 的支持。**
* `AdvancedRetrofitCallback` 新增 `onIntercepted(Call<T> call, T resp)` 方法，用于在接口返回数据被“劫持”时进行回调。
* 将 `AdvancedRetrofitCallback#onEnd(Call<T> call)` 回调放到所有其他回调方法后执行。
* `PageResult` 增加 `maxSize` 字段。

## Version 0.4

*2017-10-20*

* 新增 `ApiStatusInterceptor` ，使用户有机会对某个接口返回状态进行统一处理。
* 新增 sample module，进行简单的示例。
* 新增 HTTPS 配置帮助类 `HttpsHelper` 。
* OkHttp 版本升级到 3.9.0 ，RxJava2 版本升级到 2.1.2 。
* 将 AdvancedRetrofitCallback 接口的 onError 回调方法的返回值类型改为 void 。

## Version 0.3

*2017-07-14*

OkhttpConfiguration 接口中增加 `X509TrustManager trustManager();` 方法，用于配置 HTTPS 证书。

## Version 0.2

*2017-06-23*

* 增加 com.github.UamaHZ:retrofit-gson-converter:0.1 依赖，用于解决项目中接口报错时 data 字段数据类型和约定不一致造成的 gson 解析报错的问题。
* 升级 Retrofit 版本到 2.3.0 ，升级 Okhttp 版本到 3.8.1 。

## Version 0.1
Initial release.

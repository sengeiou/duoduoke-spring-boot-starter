# duoduoke-spring-boot-starter
多多客api

支持多多客商品、订单等api

使用：
（1）对于springboot项目，只需要导入包并新增yaml/properties配置
```
#client id 必需
duoduoke.api.client-id="your client id"
#client secret 必需
duoduoke.api.client-secret="you client secret"
#client超时时间 非必需
duoduoke.api.connection-timeout-millis=300
#request请求超时时间非必需
duoduoke.api.connection-request-timeout=300
#自定义client 需要实现com.holyw.duoduoke.client.IClient接口
#可以支持不走配置 从数据库、redis、配置中心等读取以上配置实现 非必需
duoduoke.api.client-class-name=com.holyw.client.MyDuoduokeCient
```
（2）注入duoduokeGoodsTemplate就可以方便的使用
```java
@Autowired
private DuoduokeGoodsTemplate duoduokeGoodsTemplate;
```
测试代码：
```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        ConfigurableApplicationContext applicationContext = SpringApplication.run(Application.class, args);
        DuoduokeGoodsTemplate duoduokeGoodsTemplate = applicationContext.getBean(DuoduokeGoodsTemplate.class);
        GoodsVO goodsDetail = duoduokeGoodsTemplate.getGoodsDetail(new PddDdkGoodsDetailRequestBuilder().addGoodsId("79993177108").build());
        System.out.println(goodsDetail);
    }
}
```
需要完善：

（1）自定义DefaultDuoduokeClient，失效支持redis、数据库、配置中心配置clientId clientSecret

（2）...

交流QQ：675424581

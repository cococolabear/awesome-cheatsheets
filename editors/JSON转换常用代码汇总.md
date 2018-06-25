## JSON 转换常用代码汇总

### 常用泛型的转换

```java
RespDTO<List<CasJsDataRespDTO>> respDTO = JSON.parseObject(result, new TypeReference<RespDTO<List<CasJsDataRespDTO>>>() {});
```


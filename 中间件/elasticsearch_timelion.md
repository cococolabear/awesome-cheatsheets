
```
.es(q=country:de).label(Germany)
```

```
es(q=de), .es(q=us)
```

```
.es(q=de).label(Germany), .es(q=us).label('United States')
```

![](/images/elasticsearch/1.png)


```
.es(q=country:de).label(Germany)
```

```
.es(split=country:4)
```

![](/images/elasticsearch/2.png)

```
.es(split=country:4, metric=sum:bytes)
```

![](/images/elasticsearch/3.png)

```
.es(), .static(25, label='good visitor level')
```

![](/images/elasticsearch/4.png)

```
.es().label(current), .es(offset=-1w).label('prev week')
```

![](/images/elasticsearch/5.png)

```
.es().bars(), .static(50).points(symbol=cross, radius=2), .static(60).lines(width=5)
```

![](/images/elasticsearch/6.png)

```
.es().color(#DDD), .es().mvavg(5h)
```

![](/images/elasticsearch/7.png)

```
.es().bars(stack=false).color(#F44336), .min(.es(), 25).bars(stack=false).color(#8BC34A)
```

![](/images/elasticsearch/8.png)


```
.es(),.es().if(gt, .es(offset=-1d), .es(), null).bars(3).color(#BEDB39).label(over), .es().if(lte, .es(offset=-1d), .es(), null).bars(3).color(#c66).label(under)
```

![](/images/elasticsearch/9.png)

```
.es().label(今天请求量),.es(offset=-1d).label(昨天请求量),.es().subtract(.es(offset=-1d)).label("两者差异").lines(steps=1,fill=2,width=0).color(#F44336),.min(.es().subtract(.es(offset=-1d)),0).lines(steps=1,fill=2,width=0).color(#16134a)
```

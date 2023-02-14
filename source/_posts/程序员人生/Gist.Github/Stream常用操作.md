---
title: Stream常用操作
toc: false
date: 2023-02-14 23:04:48
tags: [Stream]
---

#### List根据某个属性去重
``` java
ArrayList<SKU> skus = skuList.stream().collect(
                Collectors.collectingAndThen(
                        Collectors.toCollection(
                                () -> new TreeSet<>(Comparator.comparing(n -> n.getGid())))
                        , ArrayList::new));
```

#### 指定字段排序(升序)
``` java
orderList.stream()
    .sorted(Comparator.comparing(Order::getCreateTime))
    .collect(Collectors.toList());
```

#### 指定字段排序(降序)
``` java 
orderList.stream()
    .sorted(Comparator.comparing(Order::getCreateTime).reversed())
    .collect(Collectors.toList());
```

#### 指定字段排序(null排前面)
``` java 
List<LuckyBoysVo> luckyBoysVoList = luckyBoysList.stream()
            .sorted(Comparator.comparing(LuckyBoysVo::getUsageTime, Comparator.nullsFirst(Date::compareTo)))
            .collect(Collectors.toList());
```

#### 指定字段相同，指定值计算和
``` java
exportAgentVoList.stream()
                .collect(Collectors.groupingBy(o->(o.getGoodsId() +o.getAgentId()),Collectors.toList()))
                .forEach((id, transfer) -> {
                    transfer.stream()
                            .reduce((a,b)->
                                    new ExportAgentVo(a.getDealCode(),
                                            a.getAgentId(),
                                            a.getGoodsId(),
                                            a.getGoodName(),
                                            a.getCount() + b.getCount(), a.getName(), a.getAddress()))
                            .ifPresent(exportAgentVoListResult::add);
                });
```

#### 指定字段相同，计算相同个数
``` java
 // 根据指定字段，计算个数
        Map<String, Long> map = list.stream()
                .collect(Collectors.groupingBy(TkDetailMaskLayerMapping::getMaskId, Collectors.counting()));
```

#### 指定字段分组
``` java
Map<String, List<ExportAgentVo>> exportAgentVoMap = exportAgentVoListResult.stream()
                .collect(Collectors.groupingBy(ExportAgentVo::getAgentId));
```

#### 分组 并求和
``` java
/*
分组 并求和
Collectors.gropingBy(分组的字段,Collectors.summingInt(求和的字段))
*/              
Map<String, Integer> goodCountMap = goodsProcurementDetailVos.stream()
                .filter(a -> a.getSupplierName().equals(exportGoodsProcurementDetailVo.getSupplierName())
                        && a.getAgentId().equals(exportGoBeerVo.getAgentId()))
                .collect(Collectors.groupingBy(ExportGoodsProcurementDetailVo::getGoodsId,
                        Collectors.summingInt(ExportGoodsProcurementDetailVo::getCount)));
```

#### List转Map
``` java
List<CustomerDetailResp> result = new ArrayList<>();
Map<String, String> map = result.stream().collect(Collectors.toMap(CustomerDetailResp::getDept, CustomerDetailResp::getMembers));

// 另一种方式
Map<String, CustomerDetailResp> map = result.stream().collect(Collectors.toMap(CustomerDetailResp::getDept, CustomerDetailResp -> CustomerDetailResp));

/**
 * List -> Map
 * 需要注意的是：
 * toMap 如果集合对象有重复的key，会报错Duplicate key ....
 *  apple1,apple12的id都为1。
 *  可以用 (k1,k2)->k1 来设置，如果有重复的key,则保留key1,舍弃key2
 */
Map<Integer, Apple> appleMap = appleList.stream().collect(Collectors.toMap(Apple::getId, a -> a,(k1,k2)->k1));
```

#### List转String
``` java
String join = Joiner.on(',').join(itemNoList);
```

#### String转List
``` java
List<String> saleList = Arrays.stream(sales.split(",")).distinct().collect(Collectors.toList());
```
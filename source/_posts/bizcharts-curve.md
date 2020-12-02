---
title: bizcharts曲线图/折线图
date: 2020-12-02 11:15:30
tags: bizcharts
cover: /assets/cover-bizcharts.png
categories: 
    - [框架,bizCharts]
---
## 数据过多时，容易导致x轴标签过多，
![](1.png)
设置tickCount，减少x轴显示的标签数量
```
render() {
    const cols = {
        time: {
            range: [0, 1],
            tickCount: 8 //设置底部x轴显示个数：8个
        },
    };
    return (
        <Chart height={280} scale={cols} forceFit
            data={data}
            )
        >
        //略
        </Chart>
    )
}
```
![](2.png)

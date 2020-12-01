---
title: bizCharts饼图/环形图
date: 2020-11-30 18:10:31
cover: /assets/cover-bizcharts.png
tags: 
    - [bizCharts]
categories: 
    - [框架,bizCharts]
---

![](1.png)
## 圈内文字
### 3.x
```
<Guide>
	<Html
		position={["50%", "50%"]}
		html={`<div style="color:#8c8c8c;font-size:1.em;text-align: center;width: 10em;">异常任务量<br><span style="color:#262626;font-size:1.5em">${this.props.total}</span></div>`}
		alignX="middle"
		alignY="middle"
	/>
</Guide>
```

### 4.x
```
<Annotation.Text
	position={['50%', '40%']}
	content="异常任务量"
	style={{
		lineHeight: '240px',
		fontSize: '14',
		// fill: '#9AA39E',
		textAlign: 'center'
	}}
/>
<Annotation.Text
	position={['50%', '55%']}
	content={`${rate}`}
	style={{
		lineHeight: '240px',
		fontSize: '20',
		textAlign: 'center'
	}}
/>
```

## 图例Legend
没有图例就设

```
<Legend visible={true}>
```

### 3.x 自定义图例文字样式
3.x是通过useHtml、containerTpl和itemTpl等属性来定义
```
<Legend
	offsetX={-120}
	offsetY={20}
	position="right"
	useHtml={true}
	containerTpl="<div class=&quot;g2-legend&quot;><table class=&quot;g2-legend-list&quot; style=&quot;min-width:300px;list-style-type:none;margin:0;padding:3;&quot;></table></div>"
	itemTpl={(value, color, checked, index) => {
		// const obj = dv.rows[index];
		const obj = this.props.data[index]
		checked = checked ? "checked" : "unChecked";
		return (
			'<tr class="g2-legend-list-item item-' + index + " " + checked + '" data-value="' + value + '" data-color=' + color +
			' style="cursor: pointer;font-size: 12px;margin-top:12px;margin-bottom:15px">' +
			'<td width=220 style="border: none;padding:0;"><i class="g2-legend-marker" style="width:10px;height:10px;display:inline-block;margin-right:10px;background-color:' +
			color +
			';"></i>' +
			'<span class="g2-legend-text" style="color:rgba(0, 0, 0, 0.85);">' +
			(value.length > 13 ? value.substring(0, 13) + '...' : value) +
			"</span></td>" +
			'<td style="text-align: center;border: none;padding:3;width:60px;">' +
			obj.percent +
			"%</td>" +
			'<td style="text-align: center;border: none;padding:0;width:50px;color:rgba(0, 0, 0, 0.85),marginRight:10px">' +
			obj.num +
			"</td>" +
			"</tr>"
		);
	}}
	g2-legend={{
		width: 'max-content',
		overflow: 'unset',
		marginTop: '10px',
		marginBottom: '10px'
	}}
	g2-legend-text={{
		width: '120px',

	}}
/>
```
效果图例


### 4.x 自定义图例文字样式

在官方问当里看Lengend暂时没有找到合适的属性，于是使用onGetG2Instance属性


4.x案例：
__jsx：__
```
import React, { useEffect, useState } from 'react';
import DataSet from '@antv/data-set';
import numeral from 'numeral';
//import { dispatchRate } from '@/services/home';
import { Chart, registerShape, Tooltip,Legend, Annotation, Axis, Interval, Interaction, Coordinate } from 'bizcharts';
import { Empty ,Space, Typography,Row,Col,Button, Tooltip as AntdTooltip} from 'antd';
import styles from './index.less';
const sliceNumber = 0.01; // 自定义 other 的图形，增加两条线

registerShape('interval', 'sliceShape', {
	draw(cfg, container) {

		const { points } = cfg;
		let path = [];
		path.push(['M', points[0].x, points[0].y]);
		path.push(['L', points[1].x, points[1].y - sliceNumber]);
		path.push(['L', points[2].x, points[2].y - sliceNumber]);
		path.push(['L', points[3].x, points[3].y]);
		path.push('Z');
		path = this.parsePath(path);
		return container.addShape('path', {
			attrs: {
				fill: cfg.color,
				path
			}
		});
	}
});


const RatePieChart = (props) => {
	const [rate, setRate] = useState([]);
	const [dataSource, setData] = useState([]);
	const getdispatchRate = async () => {
		//const res = await dispatchRate();
		const d = [
				{
					type: '333',
					value: 11
				},
				{
					type: '222',
					value: 67
				},
				{
					type: '111',
					value: 5
				},
				{
					type: 'XXXXXXXX',
					value: 67
				},
				{
					type: '11',
					value: 67
				},
				{
					type: '2',
					value: 2
				},
			];
			setData(d)
			setRate(66)
	}
	useEffect(() => { getdispatchRate() }, []);
	const { DataView } = DataSet;
	const dv = new DataView();
	dv.source(dataSource).transform({
		type: 'percent',
		field: 'value',
		dimension: 'type',
		as: 'percent'
	});

	const getPercent = () => {
		let num = 0;
		if (!dv.rows) {
			return num;
		}
		dv.rows.map((item) => {
			if (item.type === '成功') {
				num = item.percent * 100;
			}
		});
		return num;
	};
	const array=[]
	const [ chart, setchart ] = useState([]);
    <!-- 设置Legend -->
	const setLegend = () => {
		let node = [];
		if (chart.length !== 0) {
			chart.geometries[0].dataArray.map((item,index) => {
				// console.log('{item[0]',item[0])
				node.push(
					<Row style={{width:280}} key={index}>
						<Col span={4}><span
								className={styles.dot}
								style={{
									backgroundColor: item[0].color,
									textAlign:'left'
								}}
							/>
						</Col>
						<Col span={12} style={{textAlign:'left'}}>
							<AntdTooltip  title={item[0]._origin.type}>
								<Typography.Text ellipsis={true} style={{width:'100%'}}>{item[0]._origin.type}</Typography.Text>
							</AntdTooltip>
						</Col>
						<Col span={8}>{item[0]._origin.value}</Col>
					</Row>
				);
			});
		}
		return <ul className={styles.legend}>{node}</ul>;
	};
	return (
		<div>
			<Row>
				<Col span={16}>
				<Chart data={dv} height={240} autoFit
					onGetG2Instance={(c) => {
						setchart(c);
				}}
				>
					<Coordinate type="theta" radius={0.8} innerRadius={0.75} />
					<Axis visible={false} />
					<Tooltip showTitle={false} />
					<Annotation.Text
						position={['50%', '40%']}
						content="执行成功预案数"
						style={{
							lineHeight: '240px',
							fontSize: '14',
							// fill: '#9AA39E',
							textAlign: 'center'
						}}
					/>
					<Annotation.Text
						position={['50%', '55%']}
						content={`${rate}`}
						style={{
							lineHeight: '240px',
							fontSize: '20',
							textAlign: 'center'
						}}
					/>
					<Interval
						adjust="stack"
						position="value"
						color="type"
						shape="sliceShape"
						color={[
							'type',
						]}
					/>
					<!-- 因为要自定义设置图例，所以图形自带的图例要隐藏，设为false -->
					<Legend visible={false}/>
					<Interaction type="element-single-selected" />
				</Chart>
				</Col>
				<Col span={8} style={{textAlign:'center'}}>
				  	{dataSource.length !== 0 ? setLegend() : ''}
				</Col>
				</Row>
			}
		</div>
	);
};
export default RatePieChart;
```

__less文件__
```
@import '~antd/es/style/themes/default.less';

.chart {
	position: relative;
}
&.hasLegend .chart {
	width: ~'calc(100% - 240px)';
}
.legend {
	position: absolute;
	top: 50%;
	left: 0;
	margin: 0 20px;
	padding: 0;
	list-style: none;
	transform: translateY(-50%);
	li {
		height: 22px;
		line-height: 22px;
		cursor: pointer;
		&:last-child {
			margin-bottom: 0;
		}
	}
}
.dot {
	position: relative;
	top: 0px;
	display: inline-block;
	width: 8px;
	height: 8px;
	margin-right: 5px;
	border-radius: 8px;
}
.line {
	display: inline-block;
	width: 1px;
	height: 16px;
	margin-right: 8px;
	background-color: @border-color-split;
}
.legendTitle {
	color: @text-color;
}
.percent {
	color: @text-color-secondary;
}
.value {
	right: 0;
}
.title {
	margin-bottom: 8px;
}
.total {
	position: absolute;
	top: 50%;
	left: 50%;
	max-height: 62px;
	text-align: center;
	transform: translate(-50%, -50%);
	& > h4 {
		height: 22px;
		margin-bottom: 8px;
		color: @text-color-secondary;
		font-weight: normal;
		font-size: 14px;
		line-height: 22px;
	}
	& > p {
		display: block;
		height: 32px;
		color: @heading-color;
		font-size: 1.2em;
		line-height: 32px;
		white-space: nowrap;
	}
}

.legendBlock {
	&.hasLegend .chart {
		width: 100%;
		margin: 0 0 32px 0;
	}
	.legend {
		position: relative;
		transform: none;
	}
}

```

__效果图：__
![](2.png)

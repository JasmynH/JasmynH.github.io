---
title: antd table的嵌套子表格组件蔽坑
date: 2020-11-02 10:59:08
tags: antd
top_img: https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1604395474516&di=5b3d068a6675d7af96d2f139b9a0f27d&imgtype=0&src=http%3A%2F%2Fb-ssl.duitang.com%2Fuploads%2Fitem%2F201810%2F28%2F20181028183440_RtJC3.thumb.700_0.jpeg
categories: react/antd
---
蚂蚁框架嵌套子表格
![蚂蚁框架嵌套子表格](https://upload-images.jianshu.io/upload_images/11060508-985034350b209e6e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 出现成功导入数据后，点击“+”号后下拉，出现的详情内容表格又会多出一个
如图：![如图](https://upload-images.jianshu.io/upload_images/11060508-4092407da1046e0d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

原代码：![原代码](https://upload-images.jianshu.io/upload_images/11060508-f401ea5538ec69c2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

将接口数据导入进外层和内层的table，点击“+”号下拉详细信息出现两个或者两个以上的子表格，警告一直显示的是“Warning: Each child in a list should have a unique "key" prop”，需要设置key值。

但是添加key值用map（）和push添加，key值显示已经添加，但依旧报原先key值的错。
```
const [dataTitle, setDataTitle] = useState([]);
  const getSearchInpTab = async () => {
    const tableRes = await SearchInpTab({group_Id:''});
    if (tableRes.code === '200') {
      const arr = []
      tableRes.data.map((item,index)=>{
              item.key = index
              arr.push(item)
            })
            setDataTitle(arr);
      // setDataTitle([...tableRes.data]);
    }
  };
```
后台修改接口，加上key值，仍然出现相同的错误。


**找了很久，发现antd的table框架里传入的数据只要有children，就会自动显示“+”号，因为接口传入的数据里，其子数据下还有children，所以就会导致点击外表格的“+”号，子表格里还会出现多个带“+”号的子表格，让后台将数据的children改成lists之后，变解决了这个问题。**
![效果图](https://upload-images.jianshu.io/upload_images/11060508-314faf2f6a4a5f2b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
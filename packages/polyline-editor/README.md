PolylineEditor 编辑器
===

Polyline 编辑器，此组件只支持AMap JS API v2.0 及以上版本。想在低版本 AMap （如 V1.4.15及以下）中使用拆线编辑功能可以查看 [PolyEditor 编辑器](/react-amap#/poly-editor)。

```jsx
import { PolylineEditor } from '@uiw/react-amap';
// 或者单独安装使用
import { PolylineEditor } from '@uiw/react-amap-polyline-editor';
```

### 基本用法

注意，需要加载 `<APILoader plugin="AMap.PolylineEditor">`，需要加载 `AMap.PolylineEditor`<!--rehype:style=background: #ffe3da;color: #ff5722;--> 插件，如果点击进入当前页面，需要 `刷新`<!--rehype:style=background: #e91e63;color: #fff;--> 页面。

```jsx
<APILoader plugin="AMap.PolylineEditor">
```
<!--rehype:style=background: #fff3b7;-->

<!--rehype:-->
```jsx mdx:preview
import ReactDOM from 'react-dom';
import React, { useState, useRef } from 'react';
import { Map, APILoader, Polyline, PolylineEditor } from '@uiw/react-amap';

const Example = () => {
  const [show, setShow] = useState(true);
  const [active, setActive] = useState(false);
  // 多边形轮廓线的节点坐标数组
  const path = [
    [116.403322, 39.920255],
    [116.410703, 39.897555],
    [116.402292, 39.892353],
    [116.389846, 39.891365],
  ];
  return (
    <>
      <button onClick={() => setShow(!show)}>
        {show ? '隐藏' : '显示'}
      </button>
      <button onClick={() => setActive(!active)}>
        {active ? '结束' : '开始'}编辑
      </button>
      <div style={{ width: '100%', height: '500px' }}>
        <Map zoom={14} center={[116.400274, 39.905812]}>
          <Polyline
            visiable={show}
            path={path}
            strokeColor="#FF33FF"
            strokeWeight={6}
            strokeOpacity={0.2}
            fillOpacity={0.4}
            fillColor="#1791fc"
            zIndex={50}
          >
            <PolylineEditor
              active={active}
              onEnd={() => {
                console.log('onEnd:>>')
              }}
              onAdjust={() => {
                console.log('onAdjust:>>')
              }}
              onAdd={() => {
                console.log('onAdd:>>')
              }}
              onAddnode={() => {
                console.log('onAddnode:>>')
              }}
            />
          </Polyline>
        </Map>
      </div>
    </>
  );
}

const Mount = () => (
  <APILoader akay="a7a90e05a37d3f6bf76d4a9032fc9129" plugin="AMap.PolylineEditor">
    <Example />
  </APILoader>
);

export default Mount;
```

### Props

| 参数 | 说明 | 类型 | 默认值 |
|--------- |-------- |--------- |-------- |
| active | 是否开启编辑功能。 | `boolean` | - |
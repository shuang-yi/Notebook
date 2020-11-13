# coast

## 基本参数

`-M`：输出边界信息

`-E`: 国家代号

## 功能

### clip 剪裁

`gmt coast -EDE -M | gmt psclip`：剪裁德国

`gmt coast -Sc -A10000`：剪裁海洋，如果不加-A，陆地上的水覆盖区域也会包含进去；同理`-Gc`剪裁陆地




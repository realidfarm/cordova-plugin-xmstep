
## 集成步骤

- 直接通过 url 安装：

        cordova plugin add https://github.com/realidfarm/cordova-plugin-xmstep.git

- 或下载到本地安装：

        cordova plugin add Your_Plugin_Path

# API

## Methods

- [rfid.openDevice](#openDevice)
- [rfid.closeDevice](#closeDevice)
- [rfid.scanCycle](#scanCycle)
- [rfid.scanCycleStop](#scanCycleStop)

## openDevice

打开串口.

    rfid.openDevice();

## closeDevice

关闭串口.

    rfid.closeDevice();

## scanCycle

读取标签.

    rfid.scanCycle();

## scanCycleStop

停止读取.

    rfid.scanCycleStop();


完整调用demo:
```js
    document.addEventListener('deviceready', function() {
        rfid.openDevice(function(data) {
            rfid.scanCycle(function(data) {
                var values = data.split(":");
				var taginfo = values[1].split("|");
				var tagno = taginfo[0];
				var step = taginfo[1];
            }, function(error) {
                alert("error:" + error);
            });
        }, function(error) {
            alert("error:" + error);
        });
    });
```
# esp32_ble_demo

* 软件环境

  如无特殊标明，默认使用 IDF 版本是 [esp-idf release/v4.4](https://github.com/espressif/esp-idf/tree/release/v4.4)

## 示例

* **ble_hid_device_demo**

  遇到两个 BLE HID 的问题

  * **如何使用 ble_hid_device_demo 让 IOS 弹出软键盘**

    在苹果键盘中， eject 键的按下是弹出和弹回软键盘的方法，但在这个 demo 有 eject 的键值，但是 report map 无 eject 的操作

    查看网上资料 eject 键应该归于 Consumer Control 中，所以仿照 volume up 等实现增加了 eject 按键

  * **ble_hid_device_demo 发送 CapsLock 键值 PC 不返回 LED 状态**

    此问题在 ble_hid_device_demo 会进行修复(Github issuse: https://github.com/espressif/esp-idf/issues/10073)

    主要是定义的 output report characteristic 不支持 write no response 方式，而 PC 正是使用此方式进行 LED 状态的输出

    patch 中调整了 report map 中 LED report 部分 items 的位置，不调换也能返回 (关于 report 描述符自己理解还有些浅)

  > **note:**
  >
  > 1、HOGP_SPEC 对于 HID 要求必须链路层加密， 所以抓空中包并不好解析出来

   

  


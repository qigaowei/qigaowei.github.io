1. 首先，在电脑的任意界面按下【Win+R】快捷键打开Windows的运行窗口，并且输入“regedit”打开电脑的注册表。
2. 然后在上方的地址栏直接复制以下信息并回车：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings
3. 新建一个“DWORD(32位)值”的选项，“FlightSettingsMaxPauseDays”
4. 然后双击这个选项，将它的基数修改为十进制，数值数据修改为“10000”，也就是推迟10000天。
5. 接着打开设置，选择Windows更新，在暂停更新的右侧，点击下拉菜单，就能够看到可推迟的周数了。


[源地址](https://mp.weixin.qq.com/s/_-KkUyMIL-6dM0x_7p-dfQ)
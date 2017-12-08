# PermissionDemo

簡介
==================================
3個步驟, 簡單解決 關於Android 6.0以上的權限問題, 有興趣 可以參考看看                                

取材自以下資源
--------
跟目前的團隊成員 Benson 學習的, 再次感謝                                  
                              
使用步驟
--------
1. 在 AndroidManifest中, 填上你需要的權限                                 
   
```xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
```                                       
   
![image](https://i.imgur.com/UWP6EtG.jpg)                                      
   
```xml
<style name="ImageTranslucentTheme" parent="Theme.AppCompat.Light.DarkActionBar">
    <item name="android:windowTranslucentStatus">true</item>
    <item name="android:windowTranslucentNavigation">true</item>
</style>
```                                       
   
![image](https://i.imgur.com/UWP6EtG.jpg)                                      
   
```xml
<style name="ImageTranslucentTheme" parent="Theme.AppCompat.Light.DarkActionBar">
    <item name="android:windowTranslucentStatus">true</item>
    <item name="android:windowTranslucentNavigation">true</item>
</style>
``` 
 


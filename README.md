# PermissionDemo

簡介
==================================
3個步驟, 簡單解決 關於Android 6.0以上的權限問題, 有興趣 可以參考看看                                

取材自以下資源
--------
跟前輩 Benson 學習的, 再次感謝                                  
                              
使用步驟
--------
1. 在 AndroidManifest中, 填上你需要的權限                                 
   
```xml
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
```                                       
   
2. 自定義一個Class, 在裡面也填上你需要的權限, 以及相關請求權限的方法                                     
   
```xml
public final class Global {

    public static final int PERMS_REQUEST_CODE = 200;

    /**
     * 你想開啟哪些權限
     * AndroidManifest中, 也要填上相關權限
     * */
    private static String[] perms = {

            "android.permission.READ_EXTERNAL_STORAGE",
            "android.permission.WRITE_EXTERNAL_STORAGE"

            /*  以下是 大部分的權限, 如果不知道該開啟哪個權限, 可以試試看先開啟大部分的權限, 然後再一個一個比對刪去
            "android.permission.ACCESS_WIFI_STATE",
            "android.permission.INTERNET",
            "android.permission.ACCESS_NETWORK_STATE",
            "android.permission.READ_EXTERNAL_STORAGE",
            "android.permission.WRITE_EXTERNAL_STORAGE",
            "android.permission.MOUNT_UNMOUNT_FILESYSTEMS",
            "android.permission.VIBRATE",
            "android.permission.GET_ACCOUNTS",
            "android.permission.USE_CREDENTIALS",
            "android.permission.RECORD_AUDIO",
            "android.permission.WAKE_LOCK",
            "android.permission.BLUETOOTH",
            "android.permission.MODIFY_AUDIO_SETTINGS",
            "android.permission.ACCESS LOCATIONEXTRA_COMMANDS",
            "android.permission.ACCESS NETWORKSTATE",
            "android.permission.ACCESS NOTIFICATIONPOLICY",
            "android.permission.ACCESS WIFISTATE",
            "android.permission.ACCESS WIMAXSTATE",
            "android.permission.BLUETOOTH",
            "android.permission.BLUETOOTH_ADMIN",
            "android.permission.BROADCAST_STICKY",
            "android.permission.CHANGE NETWORKSTATE",
            "android.permission.CHANGE WIFIMULTICAST_STATE",
            "android.permission.CHANGE WIFISTATE",
            "android.permission.CHANGE WIMAXSTATE",
            "android.permission.DISABLE_KEYGUARD",
            "android.permission.EXPAND STATUSBAR",
            "android.permission.FLASHLIGHT",
            "android.permission.GET_ACCOUNTS",
            "android.permission.GET PACKAGESIZE",
            "android.permission.INTERNET",
            "android.permission.KILL BACKGROUNDPROCESSES",
            "android.permission.MODIFY AUDIOSETTINGS",
            "android.permission.NFC",
            "android.permission.READ SYNCSETTINGS",
            "android.permission.READ SYNCSTATS",
            "android.permission.RECEIVE BOOTCOMPLETED",
            "android.permission.REORDER_TASKS",
            "android.permission.REQUEST INSTALLPACKAGES",
            "android.permission.SET TIMEZONE",
            "android.permission.SET_WALLPAPER",
            "android.permission.SET WALLPAPERHINTS",
            "android.permission.SUBSCRIBED FEEDSREAD",
            "android.permission.TRANSMIT_IR",
            "android.permission.USE_FINGERPRINT",
            "android.permission.VIBRATE",
            "android.permission.WAKE_LOCK",
            "android.permission.WRITE SYNCSETTINGS",
            "com.android.alarm.permission.SET_ALARM",
            "com.android.launcher.permission.INSTALL_SHORTCUT",
            "com.android.launcher.permission.UNINSTALL_SHORTCUT"
            */
    };

    /**
     * 請求權限
     * 当 targetSdkVersion < 23时, 运行在Android M系统以上的机器上时, google官方默认都是允许的, 第三方系统除外
     * 如果 targetSdkVersion >= 23, 运行在Android M系统以上的机器上时, 就必須要动态申请权限
     */
    public static void requestPermisions(Activity activity) {

        if (Build.VERSION.SDK_INT < Build.VERSION_CODES.M) {                                       // 如果Android的版本小於23, 就跳出requestPermisions()該方法
            return;
        }

        boolean permission = true;

        for (String perm : perms) {
            /** 先判斷是否有權限, 如果沒有權限, 就跳出 然後去申請權限 */
            permission = (activity.checkSelfPermission(perm) == PackageManager.PERMISSION_GRANTED);
            if (!permission) break;
        }

        /** 申请权限  */
        if (!permission) {
            activity.requestPermissions(perms, PERMS_REQUEST_CODE);
        }
    }
}
```                                       
   
3. 最後就是在主頁面, 請求權限
   
```xml
/** 請求權限 */
Global.requestPermisions(this);
``` 
 


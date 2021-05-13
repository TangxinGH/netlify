[9240:7252:0325/133523.225:ERROR:device_event_log_impl.cc(214)] [13:35:23.225] USB: usb_device_handle_win.cc:1056 Failed to read descriptor from node connection:连到系统上的设备没有发挥作用。 (0x1F)
 
 ---
 搞了半天，没搞定
反正 ，我将pthon 的函数线程改为继承线程类的方式就可以了。==但还是会出这个错误==。不过，mitmproxy可以继承执行了，而不是直接退出chrome后再执行。估计，函数方式的线程。。。。。我当时是debug的。pydevd_pycharm


DevTools listening on ws://127.0.0.1:62751/devtools/browser/0289393e-ec0c-4503-be08-7e86399629e1
[11044:18216:0325/134529.910:ERROR:device_event_log_impl.cc(214)] [13:45:29.910] USB: usb_device_handle_win.cc:1056 Failed to read descriptor from node connection: 连到系统上的设备没有发挥作用。 (0x1F)
Web server listening at http://127.0.0.1:8081/
Loading script .\plugin.py

我代码的顺序是 selenium 全局-》crome -> mitmproxy

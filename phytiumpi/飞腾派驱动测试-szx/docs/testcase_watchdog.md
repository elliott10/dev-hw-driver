

在开发板上执行`watchdog_test`命令，设置看门狗超时时间１秒，不喂狗。应观察到系统1秒后关机，屏幕上打印出`Bye`的字样。

```rust
fn do_watchdog_test(_args: &str) {
    let mut watchdog0 = WDT0.lock();
    watchdog0.set_timeout(1);
    watchdog0.start();
}
```



在测试机上执行测试脚本，测试脚本会检测开发板是否输出了`Bye`以验证看门狗是否生效。

```sh
pytest -v -m watchdog
```


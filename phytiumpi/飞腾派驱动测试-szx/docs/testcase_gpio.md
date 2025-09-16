被测开发板上调试灯亮灭10次。

本测例基于飞腾派的点灯实验，通过观察开发板自带的调试led灯的亮灭来验证gpio的功能。

在开发板上gpio_test命令实现如下：

```rust
// 在一个循环里，周期性反转引脚的值
fn do_gpio_test(_args: &str) {
    let mut gpio0 = GPIO0.lock();
    let p = gpio::GpioPins::p8;
    gpio0.set_pin_dir(p, true);
    for i in 0..10{
        sleep(time::Duration::from_millis(1000));
        gpio0.set_pin_data(p, data);
        println!("current data: {data}");
        data = !data;
    }
}
```

在测试机上由用户验证调试led灯是否存在周期性亮灭的现象。

```sh
pytest -s -v -m gpio # 观察调试灯是否存在周期性亮灭的现象，输入"OK"则测试通过，否则测试失败
```


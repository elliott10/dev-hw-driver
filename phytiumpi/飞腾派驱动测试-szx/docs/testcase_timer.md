timer tacho test

开发板上运行`timer_tacho_test`命令，通过转速计tacho来测试timer的功能。如果tacho接收到的值发生了变化则打印"timer test OK"，否则打印"timer test failed"。

```rust
    let mut initial_value_set = false; 
    let mut meter = 0; 
    for i in 0..100 {
        if let Some(res) = tacho.get_result() {
            if !initial_value_set {
                meter = res;
                initial_value_set = true;
                println!("Initial res = {res}");
            } else {
                println!("res = {res}");
                if res != meter {
                    println!("Timer test OK.");
                    return;
                }
            }
        }
    axstd::thread::sleep(time::Duration::from_millis(50));
    }
```

测试机上执行测试脚本，测试脚本依据测试命令输出的值判断测试是否通过。

```sh
pytest -v -m timer
```


#### arceos上的测试程序

- 实现的是spi0,无中断, poll模式, 单次收发1字节的功能.
- 功能1：执行`spi_init`初始化spi0.
- 功能2：执行`spi_test`收发4个字符，测试模式下，MISO和MOSI短接，自发自收。收发一致则打印"spi test OK."

#### linux上的测试程序

- 测试点1：执行`spi_init`，通过返回字符串验证。
- 测试点2：执行`spi_test`，通过返回字符串验证。
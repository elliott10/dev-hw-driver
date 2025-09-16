#### arceos上的dma驱动测试程序
执行`dma_test`命令，如果正常执行则输出`DMA test OK`。其测试流程如下：
1. 初始化dma驱动
2. 申请dma内存
3. 填充dma内存
4. 启动dma传输
5. 等待dma传输完成
6. 校验dma内存
7. 释放dma内存
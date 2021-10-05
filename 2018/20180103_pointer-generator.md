## ACL 2017 paper "Get To The Point: Summarization with Pointer-Generator Networks" (Python3)论文及代码解析

#### 数据集预处理后

1、得到三种数据块文件：train_000.bin, ..., train_287.bin, val_000.bin, ..., val_013.bin, test_000.bin, ..., test_011.bin，每个数据块文件有1000个例子。还有一个词表文件vocabulary

#### 运行：

    python run_summarization.py --mode=train --data_path=/path/to/chunked/train_* --vocab_path=/path/to/vocab --log_root=/path/to/a/log/directory --exp_name=myexperiment

提示：为了加速训练，可以把run_summarization.py程序里的`hidden_dim`, `emb_dim`, `batch_size`,` max_enc_steps`, `max_dec_steps`, `vocab_size`这些参数设置的比默认的小一些。

**Increasing sequence length during training**: Note that to obtain the results described in the paper, we increase the values of `max_enc_steps` and `max_dec_steps` in stages throughout training (mostly so we can perform quicker iterations during early stages of training). If you wish to do the same, start with small values of `max_enc_steps` and `max_dec_steps`, then interrupt and restart the job with larger values when you want to increase them.

### baseline mode, pointer-generator mode, and coverage

### sequence-to-sequence

1、重点问题及推导

2、引申出来的问题

3、自己没有理解的问题

4、阅读论文的重要内容

5、代码解析


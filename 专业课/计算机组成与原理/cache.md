局部性原理：
- 时间局部性：循环控制变量和累加变量
- 空间局部性：数组的顺序遍历
主存容量 $M$、cache 数据区容量 $C$、块大小/行长 $B$
主存按字节编址：每个字节都有一个唯一的地址
主存地址位数 $N_{addr}=\log_2 (M)$
块内地址/偏移量位数 $N_{offset}=\log_2 (B)$
Cache 总行数 $N_{clines}=\frac{C}{B}$
主存总块数 $N_{Mblocks}=\frac{M}{B}$
- 直接映射：
$$
N_{index}=\log_2(Nclines)
$$
$$
N_{tag}=N_{addr} -N_{index}-N_{offset}
$$
$$
\text{标记(Tag)}+\text{索引(index)}+\text{块内地址(offset)}
$$
- 全相联映射：
$$
N_{index}=0
$$
$$
N_{tag}=N_{addr}-N_{offset}
$$
$$
\text{标记(Tag)}+\text{块内地址(offset)}
$$
- N 路组相联映射
$$
N_{sets}=\frac{N_{clines}}{N_{way}}=\frac{\frac{C}{B}}{N_{way}}
$$
$$
N_{set}=\log_2(N_{sets})
$$
$$
N_{tag}=N_{addr}-N_{set}-N_{offset}
$$
$$
\text{标记(Tag)}+\text{组号(Set)}+\text{块内地址(offset)}
$$
数据容量是有效数据的总大小：
$$
C_{data}=N_{clines} \times B
$$
总存储容量指实际的物理存储空间：
$$
C_{total}=N_{clines} \times((B \times 8) + N_{tag} + N_{valid} + N_{dirty} + …)
$$
$N_{valid}$ 有效位
$N_{dirty}$ 脏位，在回写法策略下必须有
替换策略位
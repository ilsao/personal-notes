
# Step 1

tcpdump on server: `tcpdump -i eth0 -w ./lab1.pcap`

listening on port: 7777 and 7778 (open two different ternimal tab)

``` bash
iperf -s -i 1 -p 7777
iperf -s -i 1 -p 7778
```

We have to limit the flow:`tc qdisc add dev eth0 root tbf rate 1mbit burst 32kbit latency 400ms`

Use two clients to send tcp flows, we have to start the second line after the first line has ended:

```
iperf -c server -i 1 -t 20 -p 7778
iperf -c server -i 1 -t 20 -p 7777
```

# Step 2

TODO1:

``` python
if dport == 7778:
            flow1_bytes += payload_len
            flow1_start = min(flow1_start, t)
            flow1_end = max(flow1_end, t)
        elif dport == 7777:
            flow2_bytes += payload_len
            flow2_start = min(flow2_start, t)
            flow2_end = max(flow2_end, t)
```

TODO2:

``` python
flow = ("172.18.0.2", 47052, "172.18.0.3", 7777)
```

TODO3:

```python
seq_end = seq_start + plen
```

TODO4:

```python
if seq_start > expected_next:
    print(f"[GAP] frame {idx} : "
          f"expected {expected_next}, got {seq_start} "
          f"(gap {seq_start-expected_next} bytes)")
    # [TODO] case 1
    expected_next = seq_end
elif seq_end <= expected_next:
    print(f"[RETX] frame {idx} : "
          f"retransmission seq={seq_start}-{seq_end} "
          f"(len={plen})")
elif seq_end > expected_next:
    # [TODO] case 3
    expected_next = seq_end
    # print(f"seq_start = {seq_start}, seq_end = {seq_end}")
```

![[Pasted image 20251003131113.png]]

![[Pasted image 20251003131244.png]]

# Step 3

In my case, the ip addr of server is: 172.18.0.3. And the client ip addr is: 172.18.0.2.

![[Pasted image 20251003132037.png]]

use the command: `tcp.analysis.out_of_order`

then I found that there's no lost packets, this keeps the same as my code output

![[Pasted image 20251003132531.png]]


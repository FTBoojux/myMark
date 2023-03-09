# 计算机网络

### 1、TCP vs UDP
TCP和UDP都是网络通信协议，但它们在传输数据时有很大的区别。

TCP（Transmission Control Protocol）是一种面向连接的协议，它提供可靠的数据传输和错误纠正。TCP建立连接并在通信过程中维护连接状态，确保数据按照正确的顺序到达目的地。TCP协议还具有拥塞控制和流量控制的机制，可以避免网络拥塞和数据丢失。由于TCP需要建立连接、维护状态、进行错误检查等操作，因此它的开销比较大，但是数据传输的可靠性比较高，适合于需要保证数据准确性和可靠性的应用，如文件传输、电子邮件等。

UDP（User Datagram Protocol）是一种无连接协议，它不保证数据传输的可靠性和顺序性，也没有拥塞控制和流量控制的机制。UDP直接将数据包发送到目的地址，不需要建立连接和维护状态，因此开销比TCP小，速度也比TCP快。UDP适合于对数据传输效率要求比较高、但对数据准确性和可靠性要求不高的应用，如视频会议、流媒体等。

总的来说，TCP适合传输需要保证可靠性的数据，UDP适合传输对实时性要求较高的数据。
# Các funtion cần biết trong thread của Java.
Thread theo thuần việt có thể hiểu là luồng, thread và process là 2 khái niệm khác nhau.
Khi làm việc với thread thông thường quan tâm đến ba vấn đề
# Thread Pool
# Multi thread và cách điều khiển await() - notify().
# Deadlook

# Các phương thức của Thread.

suspend() : Đây là phương thức làm tạm dừng hoạt động của 1 luồng nào đó bằng các ngưng cung cấp CPU cho luồng này. Để cung cấp lại CPU cho luồng ta sử dụng phương thức <br/> resume(). Cần lưu ý 1 điều là ta không thể dừng ngay hoạt động của luồng bằng phương thức này. Phương thức suspend() không dừng ngay tức thì hoạt động của luồng mà sau khi luồng này trả CPU về cho hệ điều hành thì không cấp CPU cho luồng nữa. <br/>
resume() : Đây là phương thức làm cho luồng chạy lại khi luồng bị dừng do phương thức suspend() bên trên. Phương thức này sẽ đưa luồng vào lại lịch điều phối CPU để luồng được cấp CPU chạy lại bình thường. <br/>
stop() : Luồng này sẽ kết thúc phương thức run() bằng cách ném ra 1 ngoại lệ ThreadDeath, điều này cũng sẽ làm luồng kết thúc 1 cách ép buộc. Nếu giả sử, trước khi gọi stop() mà luồng đang nắm giữa 1 đối tượng nào đó hoặc 1 tài nguyên nào đó mà luồng khác đang chờ thì có thể dẫn tới việc sảy ra deadlock. <br/>
destroy() : dừng hẳn luồng. <br/>
isAlive() : Phương thức này kiểm tra xem luồng còn active hay không. Phương thức sẽ trả về true nếu luồng đã được start() và chưa rơi vào trạng thái dead. Nếu phương thức trả về false thì luồng đang ở trạng thái “New Thread” hoặc là đang ở trạng thái “Dead” <br/>
yeild() : Hệ điều hành đa nhiệm sẽ phân phối CPU cho các tiến trình, các luồng theo vòng xoay. Mỗi luồng sẽ được cấp CPU trong 1 khoảng thời gian nhất định, sau đó trả lại CPU cho hệ điều hành (HĐH), HĐH sẽ cấp CPU cho luồng khác. Các luồng sẽ nằm chờ trong hàng đợi Ready để nhận CPU theo thứ tự. Java có cung cấp cho chúng ta 1 phương thức khá đặc biệt là yeild(), khi gọi phương thức này luồng sẽ bị ngừng cấp CPU và nhường cho luồng tiếp theo trong hàng chờ Ready. Luồng không phải ngưng cấp CPU như suspend mà chỉ ngưng cấp trong lần nhận CPU đó mà thôi. <br/>
sleep(long) : tạm dừng luồng trong một khoảng thời gian millisecond. <br/>
join() : thông báo rằng hãy chờ thread này hoàn thành rồi thread cha mới được tiếp tục chạy. <br/>
join(long) : Thread cha cần phải đợi millisecond mới được tiếp tục chạy, kể từ lúc gọi join(long). Nếu tham số millis = 0 nghĩa là đợi cho tới khi luồng này kết thúc. <br/>
getName() : Trả về tên của thread. <br/>
setName(String name) : Thay đổi tên của thread. <br/>
getId() : Trả về id của thread. <br/>
getState(): trả về trạng thái của thread. <br/>
currentThread() : Trả về tham chiếu của thread đang được thi hành. <br/>
getPriority() : Trả về mức độ ưu tiên của thread. <br/>
setPriority(int) : Thay đổi mức độ ưu tiên của thread. <br/>
isDaemon() : Kiểm tra nếu thread là một luồng Daemon. <br/>
setDaemon(boolean): xác định thread là một luồng Daemon hay không. <br/>
interrupt() : làm gián đoạn một luồng trong java. Nếu thread nằm trong trạng thái sleep hoặc wait, nghĩa là sleep() hoặc wait() được gọi ra. Việc gọi phương thức interrupt() trên thread đó sẽ phá vỡ trạng thái sleep hoặc wait và ném ra ngoại lệ InterruptedException. Nếu thread không ở trong trạng thái sleep hoặc wait, việc gọi phương thức interrupt() thực hiện hành vi bình thường và không làm gián đoạn thread nhưng đặt cờ interrupt thành true. <br/>
isInterrupted() : kiểm tra nếu thread đã bị ngắt. <br/>
interrupted() : kiểm tra nếu thread hiện tại đã bị ngắt <br/>

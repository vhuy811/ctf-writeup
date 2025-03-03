
# [Bandit Level 0 → Level 1](https://overthewire.org/wargames/bandit/bandit1.html)
## Level Goal
The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.
## Solution
Sử dụng lệnh SSH để kết nối vào cổng 2220 cuả bandit với lệnh -p sau đó nhập mật khẩu  đã cho, dùng lệnh ls cơ bản để xem có file gì trong cổng bandit0 thấy file readme dùng lệnh cat <tên file> để đọc file lấy mật khẩu.
Các lệnh đã sử dụng :ssh,-p,ls,,cat.
# [Bandit Level 1 → Level 3](https://overthewire.org/wargames/bandit/bandit0.html)
## Level Goal
The password for the next level is stored in a file called spaces in this filename located in the home directory
## Solution
Muốn đọc một file có tên là – sử dụng lệnh cat  - -- or cat ./-
Muốn đọc file có tên có dấu cách sử dụng ngoặc or \ ví dụ h\ h\ h\
# [Bandit Level 3 → Level 4](https://overthewire.org/wargames/bandit/bandit2.html)
## Level Goal
The password for the next level is stored in a hidden file in the inhere directory.


## Solution
Sử dụng ls -al inhere/ để tìm tất cả các file sau đó tìm thấy file .hiden
-a để ko quan tâm bắt đầu với gì
-l sử dụng một định dạng danh sách dài
Sau đó dùng cat inhere/.hiden để lấy mk
# [Bandit Level 4 → Level 5](https://overthewire.org/wargames/bandit/bandit4.html)
## Level Goal
The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

## Solution
Đầu tiên chạy lệnh file inhere/* đây là lệnh để tìm tệp con người có thể đọc được sau đó thấy tệp -file07
Sau đó dùng lệnh cat inhere/-file07 để lấy mk
# [Bandit Level 5 → Level 6](https://overthewire.org/wargames/bandit/bandit5.html)
## Level Goal
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable
1033 bytes in size
not executable

## Solution
Sử dụng lệnh find . -type f -size 1033c ! -executable -exec file {} +
Lệnh trên để tìm các tệp và dấu . là để tìm kiếm từ thư mục hiện tại 
-type f là chỉ các tệp bình thường khhong phải thư mục lk,
-size 1033c là để tìm tệp có dung lượng chính xác là 1033 byte c là byte
! -executable loại trừ các tệp có quyền thực thi (executable). Dấu ! là phép toán phủ định, có nghĩa là tìm các tệp không phải là executable (không thể chạy như chương trình).
-exec file {} thực thi lệnh file đối với mỗi tệp tìm được. Lệnh file sẽ xác định loại tệp (ví dụ, văn bản, nhị phân, hình ảnh, v.v.) và in kết quả ra màn hình. Dấu {} là vị trí chèn tên tệp, và dấu + cho phép find gom nhóm các tệp lại và gọi lệnh file một lần thay vì gọi mỗi tệp một lần, giúp tối ưu hiệu suất.
You will see that inhere/maybehere07/.file2 has all of the properties required by the task
Run cat inhere/maybehere07/.file2 to get the password to the level 6
# [Bandit Level 6 → Level 7](https://overthewire.org/wargames/bandit/bandit6.html)
## Level Goal
The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size
## Solution
Sử dụng lệnh find / -user bandit7 -group bandit6 -size 33c sau đó dùng lệnh cat để lấy mk
Dùng cách trên phải mò nên bổ sung lệnh trên thì thêm  2>/dev/null
# [Bandit Level 7 → Level 8](https://overthewire.org/wargames/bandit/bandit7.html)
## Level Goal
The password for the next level is stored in the file data.txt next to the word millionth

## Solution
Tôi dùng lệnh ls để xem tệp sau đó dùng lệnh grep để tìm mk kế bên từ đc cho
Grep  “từ cần kiếm” tệp
# [Bandit Level 8 → Level 9](https://overthewire.org/wargames/bandit/bandit8.html)
## Level Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
## Solution

Tôi dùng lệnh uniq -u data.txt nhưng ko hiệu quả
Thay vào đó tôi dùng lệnh sort data.txt | uniq -u
Mật khẩu đã xuất hiện và ý nghĩa của lệnh trên là tôi sắp xếp trong tệp sau đó lấy ra 1 dòng bị lặp đúng 1 lần.
# [Bandit Level 9 → Level 10](https://overthewire.org/wargames/bandit/bandit9.html)
## Level Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## Solution

Tôi dùng lệnh strings để in ra các chuỗi kí tự nhưng có quá nhiều chuỗi kí tự và sau đó tôi dùng lệnh grep == để tìm kí tự gần dấu bằng và kết hợp strings data.txt |grep ==
# [Bandit Level 10 → Level 11](https://overthewire.org/wargames/bandit/bandit10.html)
## Level Goal
The password for the next level is stored in the file data.txt, which contains base64 encoded data


## Solution

Tôi thấy đề bài cho kiếm dữ liệu trong file bị mã hóa base64 sau đó tôi đã sử dụng câu lệnh base64 <tên tệp> nhưng không ra kết qua nên tôi sử dụng base64 –-decode <tên tệp> sau đó tôi đã lấy đc mk 
# [Bandit Level 11 → Level 12](https://overthewire.org/wargames/bandit/bandit11.html)
## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Solution

Tôi sử dụng lệnh tr để đổi kí tự và câu lệnh tổng hợp là cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' đây cũng là một dạng mã hóa có tên là Caesar Cipher
# [Bandit Level 12 → Level 13](https://overthewire.org/wargames/bandit/bandit12.html)
## Level Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Solution
ở bandit 12 có vẻ rất phức tạp tôi đã sử dụng nhiều câu lệnh giải nén vd như gzip,bzip2,tar
dùng các lệnh phụ họa như file cat mv cp    tôi còn dùng lệnh xxd để chuyển tệp sang dạng khác
lưu ý -d là để giải nén nếu thêm vào các tệp như gzip,bz2
còn lệnh tar tôi dùng  -xvf   và chân sau chấm của các lệnh theo thứ tự .gz .bz2.tar 
# [Bandit Level 13 → Level 14](https://overthewire.org/wargames/bandit/bandit13.html)
## Level Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on


## Solution
ở laps này tôi phải dùng private key để kết nối tiếp vào laps tiếp theo
tôi dùng ssh để liên kết tới cổng bandit 14 với địa chỉ bandit14@localhost và dùng thêm lệnh -i với mục đích muốn nhập private key để vượt qua bước nhập mk 
lệnh đầy đủ : ssh -i sshkey.private bandit14@localhost -p 2220
sau đó tôi dùng lệnh cat để lấy mk từ file /etc/bandit_pass/bandit14
# [Bandit Level 14 → Level 15](https://overthewire.org/wargames/bandit/bandit14.html)
## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost
## Solution
ở laps này tôi phải gửi mk cảu cấp độ hiện tại đến cấp độ tiếp theo để nhận mk và tôi dùng lệnh nc localhost 30000 sau đó nhập mk
# [Bandit Level 15 → Level 16](https://overthewire.org/wargames/bandit/bandit15.html)
## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.


## Solution
ở laps này tôi phải gửi mk cấp độ hiện tại đến cổng 30001 với giao thức ssl/tls nên tôi dùng lệnh openssl s_client -connect localhost:cổng và sau đó nhập mk để lấy mk
# [Bandit Level 16 → Level 17](https://overthewire.org/wargames/bandit/bandit16.html)
## Level Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
## Solution
Đầu tiên tôi dùng lệnh nmap để quét các cổng nmap -p31000-32000 -sV -sV với mục đích xem chi tiết các cổng hơn sau đó tôi cố dùng lệnh openssl s_client -connect localhost:31790 nhưng có lẽ với tôi không hiệu quả vì ko trả ra private key sau khi tôi nhập mật khẩu nên tôi đã dùng lệnh ncat 
Đầy đủ là ncat localhost –-ssl 31790 với ssl Lệnh này sẽ thiết lập một kết nối SSL/TLS mã hóa khi lắng nghe trên cổng và tôi có được privatekey
Sau khi có private key tôi đã thử kết nối vào sever nhưng chưa đủ khả năng nên tôi cấp thêm quyền cho tệp bằng lệnh chmod 600  <tên tệp> sau đó đã thử kết nối lại và đã vượt mk thành công
# [Bandit Level 17 → Level 18](https://overthewire.org/wargames/bandit/bandit17.html)
## Level Goal
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19
## Solution
 tôi dùng lệnh diff để lấy điểm khác nhau của 2 tệp
# [Bandit Level 18 → Level 19](https://overthewire.org/wargames/bandit/bandit18.html)
## Level Goal
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
## Solution
 tôi đọc sever từ ngoài với lệnh kết hợp ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme sau đó nhập mk
# [Bandit Level 19 → Level 20](https://overthewire.org/wargames/bandit/bandit19.html)
## Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
## Solution
Laps này muốn tôi dùng quyền của tệp bandit20-do để đọc file pass của laps 20
Tôi dùng lệnh ./bandit20-do để xem có gì xảy ra
Sau đó dùng lệnh kết hợp ./bandit20-do cat /etc/bandit_pass/bandit20 và lấy mk
# [Bandit Level 20 → Level 21](https://overthewire.org/wargames/bandit/bandit20.html)
## Level Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

NOTE: Try connecting to your own network daemon to see if it works as you think
## Solution
đầu tiên tôi phải mở một comand khác và vào lại laps 20 sau đó dung lệnh nc -lvnp để lắng nghe trên công ngẫu nhiên còn ở phía còn lại tôi dùng lệnh ./ suconnect <cổng> để kết nối và gửi mk hiện tại để lấy mk mới 
Vậy lệnh nc -lvnp là để lắng nghe và tôi nhận mk ở phần nc -lvnp
# [Bandit Level 21 → Level 22](https://overthewire.org/wargames/bandit/bandit21.html)
## Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.
## Solution
Crontab là thứ gì đó mới lạ đói với tôi sau khi tìm hiểu tôi biết được nó là lệnh dùng để lên lịch và tự động hóa các tác vụ trong hệ điều hành Unix/Linux. Nó cho phép chạy các lệnh hoặc script vào những thời điểm định trước.
Các tác vụ này gọi là cron jobs. Bạn có thể lên lịch để chúng chạy vào các khoảng thời gian như mỗi giờ, mỗi ngày, mỗi tuần, hoặc theo bất kỳ chu kỳ nào mà bạn yêu cầu.
Crontab là tệp cấu hình (file configuration) dùng để quản lý các cron jobs. Mỗi người dùng có thể có một tệp crontab riêng, trong đó chứa danh sách các cron jobs mà người đó muốn thực thi. Khi bạn chỉnh sửa crontab của mình, bạn sẽ thêm vào các dòng lệnh với thời gian thực thi cụ thể.
Lúc đầu tôi nhầm cron là một thư mục nên tôi đã dùng lệnh find crond nhưng nó đã không thực hiện vì cron là một lệnh chứ kphai là một diẻctory
Sau đó dùng đến crontab -l để đọc tất cả các cron đc thiết lập cho ng dùng hiện tại
Nhưng tôi ko có quyền đó nên đã bị từ chối 
Sau đó tôi dùng lệnh cat /etc/cron.d/ nhưng không hiệu quả vì đây ko  phải 1 tệp mà là file
Nên tôi dùng lệnh ls /etc/cron.d/ và đã thấy đc các tệp cron đang chạy
cat /etc/cron.d/cronjob_bandit22 sau lệnh này đã hiện lênh các cron ddg chạy sau đó dùng lệnh
cat /usr/bin/cronjob_bandit22.sh sau đó dùng lệnh cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv và lấy dc mk 
# [Bandit Level 22 → Level 23](https://overthewire.org/wargames/bandit/bandit22.html)
## Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
## Solution
Làm tương tự như bandit21 cho tới lệnh cat /usr/bin/cronjob_bandit23.sh
Tôi thấy có một scrip hiện lệnh tôi thực hiện theo lệnh cat /etc/bandit_pass/$bandit23 > /tmp/$mytarget
-bash: /tmp/8ca319486bfbbc3663ea0fbe81326349: Permission denied và tiếp lệnh
cat /tmp/8ca319486bfbbc3663ea0fbe81326349 sau đó lấy dc mk


# [Bandit Level 23 → Level 24](https://overthewire.org/wargames/bandit/bandit23.html)
## Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
## Solution
đầu tiên tôi tạo một file trong mục /tmp tên là kk
Sau đó tôi tạo thêm một tệp mk.txt với đường dẫn /tmp/kk
Có thêm dòng khai biến myname = bandit24
Cấp quyền cho file shll.sh bằng lệnh chmod a+x shll.sh
Trước đó dùng lệnh vi shll.sh để chép một dòng lệnh 
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/kk/mk.txt
mục đích để chép mk vào tệp mk.txt 
cấp quyền cho tệp mk.txt bằng lệnh chmod 777 mk.txt
sau đó dùng lệnh cp shll.sh /var/spool/bandit24/foo/. Để copy mk trong đg dẫn đến tệp mk.txt
đợi một chút và dung lệnh cat mk.txt để lấy mk
# [Bandit Level 24 → Level 25](https://overthewire.org/wargames/bandit/bandit24.html)
## Level Goal
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.
You do not need to create new connections each time
## Solution
ở laps này họ yêu cầu tôi phải viết một tệp scrips để duyệt qua 4 chữ số dò mã pin
họ cho tôi một cổng lắng nghe và yêu cầu tôi nhập mk của bandit24 và kèm theo 4 mã pin không thể tìm thấy chỉ có cách viết scrip để duyệt tất cả các số có 4 chữ số 
đầu tiên tôi di chuyển đến file /tmp và tạo thêm file vl và di chuyển đến file đó tạo một tệp duyet.c 
dùng lệnh touch sau đó dùng lệnh vim để viết ra một scrips bao gồm có
!/bin/bash                                                                                 // d
 bandit24=gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8//
for pin in {0000..9999}; do                                                   //
        echo "$bandit24 $pin"
done | nc localhost 30002                                  ////////////
sau đó cấp quyền chmod 777 cho tệp và chạy tệp bằng lệnh ./duyet.c
lệnh sẽ thực thi và thực hiện các câu lệnh trong scrips cho đến khi tìm đc mk cho cấp độ mới



# [Bandit Level 25 → Level 26](https://overthewire.org/wargames/bandit/bandit25.html)
## Level Goal
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

NOTE: if you’re a Windows user and typically use Powershell to ssh into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.
## Solution
 Lap này cho tôi biết thêm về lệnh more và -t của ssh nói nôm na more là để nhìn từ từ nếu trang thu nhỏ và lệnh -t của ssh là để tạo một terminal ảo để viết lệnh và lệnh đọc chủ yếu là :e <tên file>
 tôi dùng lệnh ls để kt và thấy đc private key tôi đã thử dung để đăng nhập nhưng không hiệu quả sau đó tôi dùng lệnh cat /etc/passwd | grep bandit26
để biết đc một số thông tin của bandit26 sau đó tôi thấy một file tên là /bin/…..
tôi đã truy cập file đó và đọc đc một scrip của tệp và biết đc shangbang bandit26 sài là bin/sh
tôi đã thu nhỏ màn hình và thực hiện lệnh ssh -t -i bandit26.sshkey bandit26@localhost -p 2220 /bin/sh
sau đó nhấn :e /ect/bandit_pass/bandit26
nhằm lấy mk đến cửa tiếp theo
nhưng để đến đc cổng 26 tôi ko thể nhập mk như thông thương mà vẫn sư dụng terminal ảo tôi dùng lệnh :set shell=/bin/bash mục đích định dạng lại shell cho bandit26 tahnhf bash thay vì sh
sau đó dùng lệnh :shell để truy cập thẳng vào bandit 26
# [Bandit Level 26 → Level 27](https://overthewire.org/wargames/bandit/bandit26.html)
## Level Goal
Good job getting a shell! Now hurry and grab the password for bandit27!


## Solution
Ls để xem có gì thì tôi thấy một file bandit27-do tương tự như laps 19 tôi cũng check thông tin file bằng cách dùng lệnh ./<tên file> sau đó tôi dùng danh nghĩa của file để lấy mk của nó 
./bandit27-do cat /etc/bandit_pass/bandit27    ./ là để chạy tệp
# [Bandit Level 27 → Level 28](https://overthewire.org/wargames/bandit/bandit27.html)
## Level Goal
There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27.

Clone the repository and find the password for the next level.


## Solution
Đầu tiên laps này muốn tôi học về git tôi đã dùng lệnh để tạo ra một file mơi trong /tmp tên là hah
Sau đó tôi thử các lệnh git clone với địa chỉ ssh://bandit27-git@localhost/home/bandit27-git/repo
Do không có cổng mặc định nên tôi không thể clone tài liệu của bandit27-git do đó tôi thêm cổng 
ssh://bandit27-git@localhost:2220/home/bandit27-git/repo và đã thành công , tôi nhập mk của ban dit 27 để lấy dữ lệu của git và sau đó đọc file tài liệu đã cho thấy tệp readme đọc và đc mk

# [Bandit Level 28 → Level 29](https://overthewire.org/wargames/bandit/bandit28.html)
## Level Goal
There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.
## Solution
Làm tương tự git 27 nhưng đến phần đọc tệp thì chỉ có dữ liệu bị ẩn nên dùng git log để lấy thông tin tác giả ,git branch để lấy quyền và git checkout <id tác giả> để bổ sung vào tệp bị thiếu . đã lấy mk

# [Bandit Level 29 → Level 30](https://overthewire.org/wargames/bandit/bandit29.html)
## Level Goal
There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.
## Solution
Cách thần kì nào đấy vẫn làm như tương tự đên bước đọc file thì bgio ở nhánh master ko thể biết mk nên đã đổi sang nhánh dev để lấy mk  
# [Bandit Level 30 → Level 31](https://overthewire.org/wargames/bandit/bandit30.html)
## Level Goal
There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30.

Clone the repository and find the password for the next level.
## Solution
Như cũ đến khi đọc thì chỉ là file trông thử git các vai trò ko hiệu quả nên dùng git tag thấy git tag có tệp secret dùng git show secret và lấy mk
# [Bandit Level 31 → Level 32](https://overthewire.org/wargames/bandit/bandit31.html)
## Level Goal
There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo via the port 2220. The password for the user bandit31-git is the same as for the user bandit31.

Clone the repository and find the password for the next level.
## Solution
Dùng thêm lệnh git add <tên tệp>  ,echo “content” <tên tệp>, git commit -m "Added key.txt"
Git push để lấy mk
 •  git add giúp bạn chuẩn bị các thay đổi để commit.
•  git commit -m lưu lại các thay đổi vào lịch sử commit.
•  git push đẩy các thay đổi lên kho từ xa.
•  git tag dùng để tạo các nhãn đánh dấu các điểm quan trọng trong lịch sử.
•  git log cho phép xem lịch sử các commit.
•  git branch giúp quản lý các nhánh cục bộ.
•  git branch -r hiển thị các nhánh từ xa.
•  git checkout dùng để chuyển nhánh hoặc khôi phục các file.

## Solution


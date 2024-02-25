# open port
```
sudo ufw allow 8080
sudo ufw allow 9000
```
# install Rust
```
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.1/itn-installer.sh | sudo sh

rustc --version
```
# create rust wallet 
```
rusk-wallet
#or
rusk-wallet restore

rusk-wallet export -d /opt/dusk/conf -n consensus.keys
/opt/dusk/bin/setup_consensus_pwd.sh
```
# srart rust
```
service rusk start
```
# Check the status of the Rusk service by running:
```
service rusk status
```
- Kiểm tra xem nút của bạn có đang đồng bộ hóa, xử lý và chấp nhận các khối mới hay không:
```
tail -F /var/log/rusk.log | grep " block accepted"
```
- Kiểm tra xem nút của bạn có tham gia đồng thuận và cố gắng tạo khối hay không:
```
tail -F /var/log/rusk.log | grep "execute_state_transition"
```
- Hoặc để kiểm tra xem nó có làm như vậy trong quá khứ không:
```
 grep execute_state_transition /var/log/rusk.log
```
- Để kiểm tra lỗi trong dịch vụ Rusk:
```
cat /var/log/rusk.err
```

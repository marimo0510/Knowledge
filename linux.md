# Linux

- パスワード暗号化
  ```
  sudo python -c "from passlib.hash import sha512_crypt; print sha512_crypt.encrypt('xxxxAnyPasswordxxxx')"
  ```

  ```
  ansible -i インベントリ <対象ホストグループ> -m user -a "name=<ユーザー名> password={{ '<パスワード>'|password_hash('sha512') }}"
  ```

  ```
  sudo su - ansible -c "cd $ANSIBLE_HOME; ansible common -m user -a 'name=c_user02 password='ken-0510'|password_hash('sha512')'"
  ```

- vi
  - 改行コード表示
  ```shell
  se list
  ```
  - 改行コード削除
  ```shell
  %s/\r//g
  ```


- openssl
```shell
openssl genrsa -aes256 -out server.key 2048
openssl req -new -key server.key -out server.csr
cp server.key server.key.org
openssl rsa -in server.key.org -out server.key
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
```

- ssh鍵認証
```
ssh-keygen -t rsa
cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys
```
id_rsa.pubを接続元に配る  
パーミッションを600にする

- エポック秒からの変換
date --date "@<エポック秒>"

# ジョーク
- cmatrix
curl -O http://www.asty.org/cmatrix/dist/cmatrix-1.2a.tar.gz
tar zvxf cmatrix-1.2a.tar.gz
cd cmatrix-1.2a
sudo yum install gcc make autoconf automake ncurses-devel
aclocal
autoconf
automake -a
./configure
make
sudo make install
cmatrix -ab

# 空白とコメント除外
grep -v -e '^\s*#' -e '^\s*$' filename
# Heartbeat memo

## 参考

* http://linux-ha.sourceforge.jp/wp/dl/pm-crm-setting
* http://gihyo.jp/admin/serial/01/pacemaker/0002?page=1
* http://qiita.com/tukiyo3/items/34e068fa1b4b3a46557e
* http://linux-ha.sourceforge.jp/wp/archives/3786/2
* http://linux-ha.sourceforge.jp/wp/archives/3855

これらのサイトを参考に、king のHAサーバから設定を拝借している。

## コピーしたもの

ra_memcached 及び ra_redis-simple はコピーしてきた。
pacemaker の rpm は vagrant テスト時に問題がもっとも少なかった最新版。
これより新しい版のパッケージはエラーになったり起動しなかったりするので注意。

## Ansible 用設定ファイルについて

ホスト名を持っているファイルは、後々わかりやすいように個々にファイリングしている。
omg_mem01m.crm と omg_mem01s.crm は同じファイルであり、
omg_mem01v_test.crm はその vagrant test 用のファイルで、IPアドレス及びホスト名だけが違う。


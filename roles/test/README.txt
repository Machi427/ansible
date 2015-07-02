Ansibel メモ。
主にテストしてみた結果や調べたことなど。

* 変数の優先度
http://qiita.com/atsaki/items/70f9cf594bf50b030918

なので、ホストベースで上書きしにくいため、
roles/x/vars/main.yml で値を設定するのはやめたほうがいい。

roles/x/defaults/main.yml でロール毎のデフォルトを設定し、
１つ２つなら inventory ファイルの [:vars] で上書き、
たくさんあるなら group_vars または hosts_vars で上書き（推奨）
するのがよいようだ。

$ ansible-playbook test.yml

PLAY [vagrant] ****************************************************************

TASK: [test | debug msg="vars_test01 is roles/test/vars/main.yml"] ************
ok: [localhost] => {
    "msg": "vars_test01 is roles/test/vars/main.yml"
}

TASK: [test | debug msg="vars_test02 is {{ vars_test02 }}"] *******************
ok: [localhost] => {
    "msg": "vars_test02 is host_vars/localhost"
}

TASK: [test | debug msg="vars_test03 is {{ vars_test03 }}"] *******************
ok: [localhost] => {
    "msg": "vars_test03 is inventory/vagrant"
}

TASK: [test | debug msg="vars_test04 is {{ vars_test04 }}"] *******************
ok: [localhost] => {
    "msg": "vars_test04 is group_vars/vagrant"
}

TASK: [test | debug msg="vars_test05 is {{ vars_test05 }}"] *******************
ok: [localhost] => {
    "msg": "vars_test05 is group_vars/all"
}

TASK: [test | debug msg="vars_test06 is {{ vars_test06 }}"] *******************
ok: [localhost] => {
    "msg": "vars_test06 is roles/test/defaults/main.yml"
}

PLAY RECAP ********************************************************************
localhost                  : ok=6    changed=0    unreachable=0    failed=0




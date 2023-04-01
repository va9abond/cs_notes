

`git clone` = `git checkout` + `git pull` 

checkout, pull, switch

chekout - переключение на коммиты
switch - переключение между ветками
pull = fetch + обновить рабочую копию
fetch (забрать комммиты, но не обновлять рабочую область)

```bash
git clone <url> <folder_name>
```

git stash берет stage сохраняет в отдельном кармане, текущие изменения откатывает рабочую область к предыдущему коммиту. Причем карман отделен от ветки, сохраненные в нем **изменения** доступны на других ветках. Чтобы применить, сохраненные в кармане git stash pop 

```bash
ssh-keygen -t ed25519
$ <~/folder_name/file_name>

```

Host github.com
IdentityFile ~/.ssh/<folder_name_with_special_ssh_key>

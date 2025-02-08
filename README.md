# Домашнее задание по Ansible

## Задание

1. **Запуск playbook на окружении из `test.yml`:**
    
```bash
ansible-playbook -i -i inventory/test.yml site.yml
```

![](https://github.com/V3l337/08-ansible-01-base/blob/main/ansible-playbook%20test.png)

2. Найдите файл с переменными (group_vars), в котором задаётся найденное в первом пункте значение, и поменяйте его на all default fact.
  - Изменил

3. Воспользуйтесь подготовленным (используется docker) или создайте собственное окружение для проведения дальнейших испытаний.
  - поднял 2 контейнера 

4. Проведите запуск playbook на окружении из prod.yml. Зафиксируйте полученные значения some_fact для каждого из managed host.

```bash
ansible-playbook -i -i inventory/prod.yml site.yml
```

![](https://github.com/V3l337/08-ansible-01-base/blob/main/ansible-playbook%20prod.png)

5. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились значения: для `deb` — `deb default fact`, для `el` — `el default fact`.
  - Изменил

6. Повторите запуск playbook на окружении prod.yml. Убедитесь, что выдаются корректные значения для всех хостов.
```bash
ansible-playbook -i -i inventory/prod.yml site.yml
```
   
7.При помощи ansible-vault зашифруйте факты в group_vars/deb и group_vars/el с паролем netology.
```bash
ansible-vault encrypt /root/ansible/base/playbook/group_vars/el/examp.yml
```
```bash
ansible-vault encrypt /root/ansible/base/playbook/group_vars/deb/examp.yml
```

8.Запустите playbook на окружении prod.yml. При запуске ansible должен запросить у вас пароль. Убедитесь в работоспособнос
```bash
ansible-playbook -i -i inventory/prod.yml site.yml -J
```

![](https://github.com/V3l337/08-ansible-01-base/blob/main/vault%20pass.png)

9.Посмотрите при помощи ansible-doc список плагинов для подключения. Выберите подходящий для работы на control node.
```bash
ansible-doc -t connection -l
```

10.В prod.yml добавьте новую группу хостов с именем local, в ней разместите localhost с необходимым типом подключения.
```yaml
local:
  hosts:
    localhost:
      ansible_connection: local
```  

11.Запустите playbook на окружении prod.yml. При запуске ansible должен запросить у вас пароль. Убедитесь, что факты some_fact для каждого из хостов определены из верных group_vars.
```bash
ansible-playbook -i -i inventory/prod.yml site.yml -J
```

![](https://github.com/V3l337/08-ansible-01-base/blob/main/ansible-playbook%20prod%2Blocalhost.png)











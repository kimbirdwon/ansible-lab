"실습"에 이어서...

1. ```vi file.yml```
   ```bash
   ---
   - name: "File Module"
     hosts: local
     tasks:
       - name: "Mode 755"
         file:
           path: "/home/kimsewon/tmp"
           mode: 0755
           recurse: yes
   ```
- 혹은 ```ansible-playbook file.yml``` 실행과 동시에 디렉터리 생성 원할 시
  ```bash
  ---
  - name: "File Module"
    hosts: local
    tasks:
      - name: "make directory dirA"
        file:
          path: "/home/kimsewon/tmp"
          state: directory

      - name: "Mode 755"
        file:
          path: "/home/kimsewon/tmp"
          mode: 0755
          recurse: yes
  ```

3. 디렉터리 생성
   ```bash
   mkdir -p /home/kimsewon/tmp/a
   mkdir -p /home/kimsewon/tmp/b
   mkdir -p /home/kimsewon/tmp/c
   ```

4. 디렉터리 생성 확인
   ```bash
   ls /home/kimsewon/tmp
   ```

5. ```ansible-playbook file.yml```
   ```bash
   PLAY [File Module] *****************************************************************************************************
   TASK [Gathering Facts] *************************************************************************************************ok: [127.0.0.1]
   TASK [Mode 755] ********************************************************************************************************ok: [127.0.0.1]
   PLAY RECAP *************************************************************************************************************127.0.0.1                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
   ```

6. ```ls -l /home/kimsewon/tmp```
   ```bash
   total 12
   drwxr-xr-x 2 kimsewon kimsewon 4096 Feb  4 10:42 a
   drwxr-xr-x 2 kimsewon kimsewon 4096 Feb  4 10:42 b
   drwxr-xr-x 2 kimsewon kimsewon 4096 Feb  4 10:42 c
   ```

7. ```vi file.yml```
   ```bash
   ---
   - name: "File Module"
     hosts: local
     tasks:
       - name: "Mode 755"
         file:
           path: "/home/kimsewon/tmp"
           mode: 0755
           recurse: yes
   ```

9. ```ansible-playbook file.yml```
   ```bash
   PLAY [File Module] *****************************************************************************************************
   TASK [Gathering Facts] *************************************************************************************************ok: [127.0.0.1]
   TASK [Mode 750] ********************************************************************************************************changed: [127.0.0.1]
   PLAY RECAP *************************************************************************************************************127.0.0.1                  : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
   ```

10. ```ls -l /home/kimsewon/tmp```
    ```bash
    total 12
    drwxr-x--- 2 kimsewon kimsewon 4096 Feb  4 10:42 a
    drwxr-x--- 2 kimsewon kimsewon 4096 Feb  4 10:42 b
    drwxr-x--- 2 kimsewon kimsewon 4096 Feb  4 10:42 c
    ```

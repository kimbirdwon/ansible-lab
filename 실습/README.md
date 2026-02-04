환경: WSL Ubuntu

1. AWS EC2 생성
2. Ansible 설치
   ```bash
   sudo apt update
   sudo apt install -y ansible
   ```
3. 디렉토리 구조 설정
   ```bash
   mkdir ~/ansible-lemp && cd ~/ansible-lemp
   ```
   
4. vi ansible.cfg
   ```bash
   [defaults]
   inventory=./inventory
   host_key_checking=False
   remote_user=ubuntu
   ```

5. vi inventory
   ```bash
   [local]
   127.0.0.1 ansible_connection=local

   [aws]
   aws1 ansible_host=43.200.175.153 ansible_user=ubuntu ansible_ssh_private_key_file=kim-key.pem
   ```
   - ansible_host=EC2 퍼블릭 IP 주소

6. 키페어 복사
   ```bash
   cp "/mnt/c/Users/k-com/Downloads/kim-key.pem" ./
   chmod 400 kim-key.pem
   ```

8. ```ansible aws -m ping```

9. ```vi lemp.yml```

10. ```ansible-playbook lemp.yml --ask-become-pass```

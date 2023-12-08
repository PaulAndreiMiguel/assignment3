# Assignment3p2

## File Locations

### Backend Binary (hello-server)

- Path: `/var/www/backend`

### Frontend (index.html)

- Path: `/var/www/my-site/index.html`

### Nginx Configuration File (hello.conf)

- Path: `/etc/nginx/sites-available/hello.conf`

### Service File for Backend (hello-server.service)

- Path: `/etc/systemd/system/hello-server.service`

### Cloud Config Script (cloud-config.yml)

```
Copy code
#cloud-config
# You will need to edit this file before creating your new servers
users:
  - name: web
    primary_group: web
    groups: sudo
    shell: /bin/bash
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ssh-authorized-keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCyvtyzNerCk+CcpFCidPMnFsQSzOundFC0Zjk4wsTn4TUdYDrJKjRqjk78/OSvn2S7lNiSOwYg39VIGYebuxm/YwwycVgB+iFCyG4OfgDi6Vsi5YiyG79HPuL26OA1nugi16KkcGYYdfeteOaai2RqOjB8QwlqMNXvILrBpbzMAY16KRA2ewErwihjrDdhSDq1kqrF5mTFeaapP639j2ghGLjGduna2AfchmQqhNEnP8M87oouecWBP2Sic4RRLCxOqbTKCuq0Gl8hebvtjTP5MGN/bmABKGSy3ce1Ya+yerLfoZzk8p0u/qcDs7ou2ZnzCv4FEZh79T8uWyRp+5LHpqVlDRZ4HaXUucnRotguxKN7BDgnTEaFGfue/OFZvjEZIQVrE6C/Jmi8KzgL7G/yycEGoa7ZPokLOqBkL5+bgx8C1yjQ+yrp+Xv4Oq9ETnF9JjLdN+BgK9e5cNxlA3+KUBGqK1igCxn0cGg4755j9t/d+7u9oY4UI4oxSRVy5hE= user@ROGgy andreimiguel96@gmail.com

packages:
  - ripgrep
  - rsync
  - nginx
  - ufw

runcmd:
  - sed -i 's/^#\(Storage=auto\)/\1/' /etc/systemd/journald.conf
  - sed -i -e '/^PermitRootLogin/s/^.*$/PermitRootLogin no/' /etc/ssh/sshd_config
  - systemctl restart ssh
  - systemctl restart systemd-journald
  - ufw allow ssh
  - ufw allow http
  - ufw enable
```

### Example Curl Commands (curl.md)

#### Testing Front-end

```
curl http://137.184.244.94
```

#### Testing Backend

```bash
curl http://137.184.244.94/hey
```

```
curl -X POST -H "Content-Type: application/json" \
  -d '{"message": "Hello from your server"}' \
  http://137.184.244.94/echo
```

# SSH-Enabled Ubuntu Docker Images + Ansible core control image + docker-compose

## Usage

### Cloning the Repository

To get started, clone the GitHub  [repository](https://github.com/gabrielpose/ansible_lab.git)) containing the Dockerfiles, docker-compose:

```bash
git clone (https://github.com/gabrielpose/ansible_lab.git)
cd ubuntu-sshd
```

### Building the Docker Images

Build the Docker images from within the cloned repository directory:

```bash
### Build ubuntu_ssh image
docker build -t my-ubuntu_sshd:latest -f ./Dockerfile_ubuntu .
### Build ubuntu with ansible core ansible_core image
docker build -t ansible-core:latest -f ./Dockerfile_ansible .
```
### Data volume mapped on ansible-core
To provide a volume that contains the ansible configuration folder, a volume named data-volume is mounted in /data at ansible-core image.
This provide access to files within this container as an easy way to open from host machine to edit files in any IDE or VisualStudioCode

    volumes:
      - .\ansible_core\data-volume:/data

### Running 2 ubuntu containers and ansible-core

```bash
docker-compose up -d
```

### Pre-configured user ###
user: ansible
pass: ansible

### SSH Access

```bash
ssh -p 2221 ansible@127.0.0.1 (ubuntu_ssh1)
ssh -p 2222 ansible@127.0.0.1 (ubuntu_ssh2)
ssh -p 2223 ansible@127.0.0.1 (ansible-core)
```


## License

This Docker image is provided under the [MIT License](LICENSE).

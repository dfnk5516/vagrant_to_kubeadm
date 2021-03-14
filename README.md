# Vansible with Kubespray

## 소개

쉽고 빠른 Docker+Kubernetes 개발, 학습 및 강의 환경 구축을 위해 설계된<br/>
Vagrant, Ansible, Kubespray를 사용한 IaC(Infra as Code) 도구

## 사용 전 필요 조건

사용자의 환경에 [Vagrant](https://www.vagrantup.com/downloads)와 [VirtualBox](https://www.virtualbox.org/wiki/Downloads)가 미리 설치되있어야 한다.

## 사용 방법

<span>1.</span> [.env](.env) 파일을 구성한다.

<span>2.</span> kubespray를 수동으로 구성하고 싶다면, [CLUSTER_STRUCTURE_AUTO_CREATE=no](.env#L38)으로 옵션을 설정하고,
[cluster folder](cluster) 를 목적에 맞게 구성한다.

<span>3.</span> [Vagrantfile](Vagrantfile)이 위치한 경로에서 하단의 명령어를 bash 쉘에 입력한다.

```sh
$ vagrant plugin install vagrant-env vagrant-vbguest
$ vagrant up
$ vagrant ssh $(vagrant status | tail -5 | sed -n '1p' | awk '{ print $1}') // 기본 설정 $ vagrant ssh m1
```

## 참고 사항

몇 가지 alias가 자동 등록된다.

```
alias ans='ansible'
alias anp='ansible-playbook'
alias k='kubectl'
```

## 문제 해결

<span>1.</span> 프로비전이 실패한 경우 **vagrant provision** 명령어로 이를 다시 시도한다.

<span>2.</span> **vagrant destroy --force && vagrant up** 와 같이 가상머신을 삭제하고 다시 생성할때,<br/>
간혹 정상적으로 삭제된 것으로 보이지만 실제로는 삭제되지 않아서 실패하는 경우가 있으므로 버추얼 머신 환경설정의 가상머신 파일 저장 경로에서 이를 직접 확인해서 삭제 후 다시 시도한다.

<hr/>

## Introduce

IaC (Infra as Code) tool designed for easy and fast Docker + Kubernetes development, learning, and lecture environment construction<br/>
with using Vagrant, Ansible, Kubespray.

## Requirements before use

[Vagrant](https://www.vagrantup.com/downloads) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads) must be installed in the user's environment in advance.

## How to Use

<span>1.</span> Configure the [.env](.env) file.

<span>2.</span> If you want to configure kubespray with manually, set [CLUSTER_STRUCTURE_AUTO_CREATE=no](.env#L38)
then configure the [cluster folder](cluster).

<span>3.</span> Type the following command into the bash shell in the path where the [Vagrantfile](Vagrantfile) is located.

```sh
$ vagrant plugin install vagrant-env vagrant-vbguest
$ vagrant up
$ vagrant ssh $(vagrant status | tail -5 | sed -n '1p' | awk '{ print $1}') // By default, $ vagrant ssh m1
```

## Note

Several aliases are automatically registered.

```
alias ans='ansible'
alias anp='ansible-playbook'
alias k='kubectl'
```

## Trouble Shooting

<span>1.</span> If provisioning fails, try again with the **vagrant provision** command.

<span>2.</span> When deleting and recreating a virtual machine like **vagrant destroy --force && vagrant up**,<br/>
it appears to have been deleted normally, but it is not actually deleted once at a time. Check it yourself, delete it, and try again.

<hr/>

## 개인 문서, Private Documents

### [https://github.com/rayshoo/vansible_with_kubespray/wiki](https://github.com/rayshoo/vansible_with_kubespray/wiki)

<hr/>

## 공식 문서, Official Documents

### [Vagrant](https://www.vagrantup.com/docs)

### [Ansible](https://docs.ansible.com/)

### [Docker](https://docs.docker.com/)

### [Kubernetes](https://kubernetes.io/ko/docs/home/)

<hr/>
 
## 참고한 책, Book referenced

카와무라 세이고,기타노 타로오,나카야마 타카히로,구사카베 타카아키,리쿠르트 테크놀로지<br/>
번역 양성건,영진닷컴(2020),IT 운용 체제 변화를 위한 데브옵스

정원천,공용준,홍석용,정경록,동양북스(2020),쿠버네티스 입문

<hr/>

## 참고한 곳, Site referenced

### Shell script

[핸드오버,일상 메모장](https://hand-over.tistory.com/32)<br/>
[양햄찌가 만드는 세상](https://jhnyang.tistory.com/146)

### ruby<br/>

[조묵헌,Ruby 처음 배우기:데이터타입](https://smartbase.tistory.com/47)<br/>
[yundream,Joinc](https://www.joinc.co.kr/w/Site/Ruby/File)

### vagrant<br/>

[asdf,노력 이기는 재능 없고 노력 외면하는 결과도 없다](https://m.blog.naver.com/PostView.nhn?blogId=sory1008&logNo=220759961657&proxyReferer=https:%2F%2Fwww.google.com%2F)<br/>
[YOUNG.K](https://rangken.github.io/blog/2015/vagrant-1/)

### ansible<br/>

[세모데](https://semode.tistory.com/m/164)<br/>
[Sentimental Programmer](https://yoonbh2714.blogspot.com/2020/09/ansible-ssh-password.html)<br/>
[부들잎의 이것저것](https://forteleaf.tistory.com/entry/ansible-%EC%9E%90%EB%8F%99%ED%99%94%EC%9D%98-%EC%8B%9C%EC%9E%91)<br/>
[mydailytutorials,Working with Environment​ Variables in Ansible](https://www.mydailytutorials.com/working-with-environment%E2%80%8B-variables-in-ansible/)<br/>
[How to create a file in ansible](https://phoenixnap.com/kb/ansible-create-file)

### python j2 template<br/>

[Python2.net](https://www.python2.net/questions-962144.htm)<br/>

### kubespray<br/>

[브랜든의 블로그](https://brenden.tistory.com/109)<br/>
[alice_k106님의 블로그](https://m.blog.naver.com/PostView.nhn?blogId=alice_k106&logNo=221315933945&proxyReferer=&proxyReferer=https:%2F%2Fwww.google.com%2F)<br/>
[teamsmiley 블로그](https://teamsmiley.github.io/2020/09/30/kubespray-01-vagrant/)<br/>

### lecture<br/>

[조훈,다양한 환경을 앤서블(Ansible)로 관리하기 with 베이그런트(Vagrant)](https://www.inflearn.com/course/ansible-%EC%9D%91%EC%9A%A9/dashboard)<br/>

### git repository<br/>

[kairen/kubeadm-ansible](https://github.com/kairen/kubeadm-ansible)<br/>
[kubernetes-sigs/kubespray](https://github.com/kubernetes-sigs/kubespray)<br/>
[tpope/vim-pathogen](https://github.com/tpope/vim-pathogen)<br/>
[chase/vim-ansible-yaml](https://github.com/chase/vim-ansible-yaml)

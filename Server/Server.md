# Server

## SSH(Secure Shell) Protocol

네트워크 상에 연결된 다른 컴퓨터에 로그인하거나 원격에서 명령을 실행하고 시스템설정 및 파일관리를 할 수 있도록 도와주는 응용프로그램(프로토콜)

VPN을 구성하는 것보다 가격이 저렴하고 쉽게 연결할 수 있어 많이 사용됨

포트는 기본적으로 22포트

SSH를 사용해야 하는 이유는 이름처럼 Secure하기 때문에 통신이 노출되더라도 암호화된 문자가 보이게되어 보안상 안전

크게 3가지를 제공한다.

### 1. Authentication

SS는 public key와 private key를 사용하는 비대칭 암호방식을 사용. 간단히 설명하면 public key와 private key가 모두 있어야 인증이 되는 방식. 각자 private key는 외부유출없이 가지고 있고 public key만 네트워크를 통해 전달한다. SSH는 RSA, DSA등 다양한 인증방식 지원

```jsx
$ ssh-keygen
$ cat !/. ssh/id_rsa.pub
```

ssh-keygen 명령어를 통해 ssh키를 생성하고 ~/. ssh/id_rsa.pub에서 public key를 확인 가능

### 2. Encryption & Integrity

SSH는 네트워크를 통해 전달되는 데이터를 암호화한다. 3DES, blowfish 등 여러가지 암호화 방식을 제공하며, 새로운 암호화 기법을 추가할 수도 있다.

그리고 SSH는 네트워크를 통해 받은 데이터가 변경되지 않았음(무결성)을 보장해준다. 이를 위해 MAC(Message Authentication Code)이라는 알고리즘을 사용

MAC 알고리즘은 다음과 같이 동작한다. SSH 클라이언트가 서버로 메세지를 보내면, MAC 알고리즘을 통해 secret key를 입력받아 MAC 코드를 생성한다. 그리고 임의길이의 암호화된 메시지와 MAC 코드를 SSH 서버로 보낸다.

서버에서는 다시 메시지와 서버의 secret key를 조홥하여 MAC 코드를 만들고, 클라이언트로부터 받은 MAC 코드와 비교하여 인증을 진행하게 된다.

### 4. Compression

SSH는 네트워크 상에서 데이터를 전송하고 수신할 때 압축과정을 거친다. 이를 통해 전송데이터의 크기를 줄여 네트워크 비용을 낮출 수 있다.

## SSH Tunneling

SSH Tunneling은 터널을 통해 데이터를 주고받는다 해서 붙여진 이름이다. 앞서 얘기했던 것처럼 연결, 통신은 모두 암호화되며 SMTP, IMAP 등 여러가지로 사용될 수 있다.

Direct로 보내면 네트워크 층에서 수많은 공격을 받을 수 있기 때문에 SSH를 통해 다른 Application에 연결하는것이 안전하다. SSH Tunneing에는 다음과 같이 두가지 방법이 있다.

### Local Port Forwarding

```jsx
$ ssh -L port1:host_name:port2 server_name
```

로컬에서 서버에 있는 MySQL과 SSH연결을 한다고 가정해본다. Local port forwarding은 로컬에 설치된 MySQL 클라이언트의 3306포트가 연결된 SSH Tunnel을 거쳐 서버에 있는 MySQL서버의 3306포트와 연결된다. 이를통해 직접 서버의 데이터베이스에 안전하게 접근할 수 있으며 요청을 보내서 서로 데이터를 주고 받을 수 있다.

### Remote Port Forwarding

```jsx
$ ssh -R port1:host_name:port2 server_name
```

이번에는 로컬에서 파이썬 웹 어플리케이션을 개발중인데 친구에게 보여주고 싶다고 가정해본다. 아직 공개 IP 주소를 제공하지 않기 때문에 인터넷을 통해 직접 기기에 연결할 수 없을 것이다. 라우터에서 NAT를 구성하여 해결할 수 있지만 라우터의 구성을 변경해야 하무로 번거롭다. 이럴때 Remote port forwarding을 통해 쉽게 해결할 수 있다.

먼저 port1의 서버에서 port2로 로컬 트래픽을 전달하는 SSH 터널을 생성한다. 이후 로컬에서 port2의 서버에 연결하면 실제로 SSH 터널을 통해 데이터를 요청하는 것을 확인할 수 있다.

OSI7계층에서 생각해보면 SSH는 Application - Transport - Network 계층에 걸쳐있다. Application 계층에서 포트를 연결하면 Transport 계층의 TCP 통신을 통해 전달되고, Network계층을 통해 목적지로 이동하게 된다.

⇒따라서 터널링은 포트포워딩 기술을 사용해서 특정 IP 또는 패킷을 전용포트로 포워딩 해주는 것

ex) A에서 C서버로 접속하려고 할때 바로 A에서 C로 접속은 불가능하고 B라는 중간서버가 존재하고 B에서는 C가 접속이 되므로 A→B→C로 접속이 되도록 하는것

### ++ 포트포워딩

외부의 특정 포트로 접속하면 내부의 특정포트로 연결해주는 기능

예를들어 외부아이피는 211.211.211.1이고 내부 서버 아이피는 192.168.1.10이라면 포트포워디 설정에서 211.211.211.1:1821 → 192.168.1.10:21로 설정했을 때 외부에서 211.211.211.1:1821로 접속하면 내부 192.168.1.10:21로 접속되는 것
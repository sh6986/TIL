# AWS

아마존이 제공하는 클라우드 서비스

기초적인 서비스들의 개념

![AWS%20b6329b025cb5483690a80253f4583850/Untitled.png](AWS%20b6329b025cb5483690a80253f4583850/Untitled.png)

유저가 우리의 서비스에 들어오면 AWS에 있는 데이터센터 중에서 우리가 구입한 만큼의 기능을 가진 서비스에 접근하는 것이다.

우리가 구입한 부분을 모아둔 것을 VPC라고 생각하자

### VPC(virtual private cloud)

페이스북 - 내 페이지의 관계가 AWS - VPC의 관계라고 생각하면 된다.

즉, 내가 등록한 무언가를 전체공개할지, 특정사람에게만 공개할지, 어떤것을  등록할지 모아둔 나만의 개인적인 공간으로 security의 제약을 줄 수가 있다.

페이스북 내에서 내 포스트를 등록하듯이 VPC안에서 등록하는 내 가상 컴퓨터의 가장 대표적인것이 EC2이다.

### EC2(elastic cloud compute)

그냥 컴퓨터라고 생각하면 된다.

컴퓨터에 보통 cpu, os, 하드웨어, RAM, 네트워크카드, 방화벽 등이 있듯이 가상의 공간(실제 데이터베이스)에 나만의 컴퓨터를 등록하는 것이다.

주로 우리가 웹사이트를 개발하기 위한 코드를 만들면 그 코드를 넣어두고 동작하게 하는  컴퓨터(웹 호스팅 서버)로 사용한다.

이외의  대표적인 AWS 서비스로 RDS와 S3라는 것이 있다.

### RDS(Relational Database Service)

관계형 데이터베이스를 서비스하는 기능이다.

### S3(Simple Storage Service)

영화, 비디오, 이미지 등 파일을 저장해두는 기능을 제공하는 서비스이다.

방대한 양을 오래동안 안전하게 보관하고 사용할 수 있다.
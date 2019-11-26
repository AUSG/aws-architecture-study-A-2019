# Linux 가상 머신 시작 - Amazon EC2 사용



## EC2 

: [Amazon Elastic Compute Cloud](https://aws.amazon.com/ko/ec2/)는 클라우드에서 가상 머신을 만들고 실행하는 데 사용하는 Amazon Web Services

AWS에서는 이러한 가상 머신을 **인스턴스** 라고 한다.

[Amazon Lightsail로 가상 머신을 빠르게 시작하기 >>](https://lightsail.aws.amazon.com/ls/webapp/home/resources)



1. Amazon EC2 ->  Launch Instance. 가상 머신을 생성 및 구성 
2. Amazon 머신 이미지(AMI)를 선택 -> 인스턴스 유형 선택 -> 설정 검토 ->키 페어 create 후 다운 -> 인스턴스의 상태 확인 -> running. 퍼블릭 IP 주소가 표시됨 
3. 인스턴스를 시작한 후 SSH를 사용해 이에 **연결** 
4. 인스턴스 종료



+ AMI : 사전에 구성된 서버 템플릿. 인스턴스를 시작하는데 사용할 수 있다. 각 AMI 에는 운영체제가 포함되어 있으며 애플리케이션과 애플리케이션 서버도 포함될 수 있다.

+ 키 페어 : SSH를 통해 Linux 인스턴스에 안전하게 액세스하는 데 사용된다. AWS에서는 키 페어의 퍼블릭 부분을 저장하며 이는 집의 잠금장치와 같다. 사용자는 키 페어의 프라이빗 부분을 다운로드하여 사용할 수 있으며 이는 집 열쇠와 같다.

  + Mac/Linux 사용자: 키 페어를 홈 디렉터리의 .ssh 하위 디렉터리에 저장하는 것이 좋다(예: ~/.ssh/MyKeyPair.pem).

    팁: MacOS에서는 기본적으로 키 페어가 다운로드 디렉터리에 다운로드 된다. 키 페어를 .ssh 하위 디렉터리로 이동하려면 터미널 창에 mv ~/Downloads/MyKeyPair.pem ~/.ssh/MyKeyPair.pem 명령을 입력한다.

+ 연결

  + Mac/Linux 사용자 : 터미널 창을 연다.

  + SSH를 사용하여 인스턴스에 연결한다. 이 사례에서는 사용자 이름이 ec2-user이고, SSH 키는 3단계 파트 d에서 저장한 디렉터리에 보관되어 있으며, IP 주소는 3단계 파트 f에서 적어두었다. 

    ```terminalOutput
    ssh -i {full path of your .pem file} ec2-user@{instance IP address}
    ```

    다음과 같이 입력한다.

    ```terminalOutput
    ssh -i 'c:\Users\yourusername\.ssh\MyKeyPair.pem' ec2-user@{IP_Address}
    ```

    예: ssh -i 'c:\Users\adamglic\.ssh\MyKeyPair.pem' ec2-user@52.27.212.125

    다음과 유사한 응답이 표시된다.

    ```terminalOutput
    The authenticity of host 'ec2-198-51-100-1.compute-1.amazonaws.com (10.254.142.33)' can't be established. RSA key fingerprint is 1f:51:ae:28:df:63:e9:d8:cf:38:5d:87:2d:7b:b8:ca:9f:f5:b1:6f. Are you sure you want to continue connecting (yes/no)?
    ```

    **yes**를 입력하고 **Enter** 키를 누른다.

  + 다음과 유사한 응답이 표시됩니다.

    ```terminalOutput
    Warning: Permanently added 'ec2-198-51-100-1.compute-1.amazonaws.com' (RSA) to the list of known hosts.
    ```

    그런 다음 인스턴스 환영 화면이 표시되면, 이제 클라우드의 AWS Linux 가상 머신에 연결된 것이다.

  

  

  ![스크린샷 2019-11-26 오후 4.31.02](/Users/dahyun/Documents/Screenshot/스크린샷 2019-11-26 오후 4.31.02.png)





+ 마무리

  

  + Amazon EC2를 사용하여 클라우드에서 인스턴스를 시작, 구성, 연결 및 종료하는 방법을 배웠습니다.
  + Amazon EC2는 클라우드에서 안전하고 크기 조정이 가능한 컴퓨팅 파워를 제공하는 웹 서비스입니다. 개발자가 더 쉽게 웹 규모의 클라우드 컴퓨팅 작업을 할 수 있도록 설계되었습니다. 웹 사이트 및 웹 애플리케이션, 개발 및 테스트 환경, 심지어 백업 및 복구 시나리오를 비롯하여 다양한 애플리케이션에 Amazon EC2를 사용할 수 있습니다. Amazon EC2는 CPU, 메모리, 스토리지 및 네트워킹 용량의 다양한 조합으로 이루어진 다양한 인스턴스 유형을 제공하므로 애플리케이션의 고유한 요구 사항에 맞춰 사용할 수 있습니다.
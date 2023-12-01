# Operating-System-Project


## producer-consumer 프로그램

### 1. 프로그램 소개

레스토랑에 손님이 들어와 주문을 하면 해당 요리사가 주문을 받아 조리하는 것을 멀티 쓰레드를 이용하여 구현하였다. 주문을 전달받지 못한 요리사가 조리를 시작하는 지점이 바로 race condition이 발생한 지점이다. 이 프로그램에서 손님의 주문은 생산된 item을, 요리사의 번호는 buffer의 index를 의미한다.

*****

### 2. 파일명

Producer_Consumer.c: 동기화 기능이 없는 producer-consumer 프로그램

Syn_Producer_Consumer.c: 동기화 기능이 추가된 producer-consumer 프로그램

*****

### 3. 실행 방법

<Producer_Consumer.c>

1. vi Producer_Consumer.c 로 코드 작성

2. gcc Producer_Consumer.c 로 컴파일

3. ./a.out 로 파일 실행


<Syn_Producer_Consumer.c>

1. vi Syn_Producer_Consumer.c 로 코드 작성

2. gcc Syn_Producer_Consumer.c 로 컴파일

3. ./a.out 로 파일 실행

*****

## Reader-Writer 프로그램

### 1. 프로그램 소개

교수님이 학생 한명의 과목 성적을 계속해서 수정하고, 해당 학생은 성적을 계속하여 열람하는 것을 프로그램으로 구현하였다. 학생이 성적을 열람하였을 때 최근 수정된 성적이 아닌 다른 성적을 읽게 되면 그 지점이 바로 race condition이 발생한 지점이다. 

*****

### 2. 파일 설명

Reader_Writer.c: 동기화 기능이 없는 reader-writer 프로그램

Syn_Reader_Writer.c: 동기화 기능이 추가된 reader_writer 프로그램

*****

### 3. 실행 방법

<Reader_Writer.c>

1. vi Reader_Writer.c 로 코드 작성

2. gcc Reader_Writer.c 로 컴파일

3. ./a.out 로 파일 실행

<Syn_Reader_Writer.c>

1. vi Syn_Reader_Writer.c 로 코드 작성

2. gcc Syn_Reader_Writer.c 로 컴파일

3. ./a.out 로 파일 실행

*****

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

### 4. 코드

<Producer_Consumer.c>
```
/* Producer & Consumer without Synchronization */
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <time.h>
#include <semaphore.h>
#include <unistd.h>
#define BUFFER_SIZE 20
void *producer(void* arg);
void *consumer(void* arg);

int buffer[BUFFER_SIZE] = {0};
int in = 0;
int out = 0;
int counter = 0;
int next_produced = 0;
int next_consumed;


int main()
{

    int pId, cId;
    pthread_t p[3];
    pthread_t c[3];

    printf("**********영업 시작**********\n");
    
    for(int i = 0; i < 3; i++)
    {
        pId = pthread_create(&p[i],NULL,(void *)producer,(void*)&i);

        if(pId < 0){
            perror("thread create error : ");
            exit(0);
        }    

        cId = pthread_create(&c[i],NULL,(void *)consumer,(void*)&i);

        if(cId < 0){
            perror("thread create error : ");
            exit(0);
        }

    }
    
    for(int i = 0; i < 3; i++)
    {
        pthread_join(p[i],NULL);
        pthread_join(c[i],NULL);
    }

    printf("**********영업 끝**********\n");

    return 0;
}


// 음식을 요리사에게 주문하는 producer 함수 
void *producer(void* arg)
{
    
    for(int i=0; i<4; i++){
        buffer[in] = next_produced;

        printf("%d번째 주문을 %d번 요리사에게 전달\n", next_produced, in);

        in = (in + 1) % BUFFER_SIZE;
        next_produced++;
        sleep(1);
        counter++;
    }
    
}


// 주문된 내역을 요리사가 조리하는 consumer 함수 
void *consumer(void* arg)
{
    
    for(int i=0; i<4; i++){
        next_consumed=buffer[out];

        printf("%d번째 주문을 %d번 요리사가 조리\n", next_consumed, out);

        out = (out + 1) % BUFFER_SIZE;
        sleep(1);
        counter--;
    }

}
```
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

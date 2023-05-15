### 👾 painterly rendering : 사진을 사람이 그린 그림처럼 바꿔주는 기법

<hr/>

### 🤖 resource 

- opencv
```#include<opencv2/opencv.hpp> ```
- 구조체 선언
```c
typedef struct Point {
	int x;
	int y;
	struct Point* link;
}Point;
//stroke 형 구조체 선언
typedef struct Stroke { 
	int r; // 원의 반지름
	Point* pt; // point 구조체를 불러옴
	CvScalar g; // 색상값을 저장
	struct Stroke* link; // 다음 값을 가르키는 링크
}Stroke;

```
- 논문의 의사코드를 활용

<img src="https://velog.velcdn.com/images/seunghyun0522/post/17a6e6c9-166e-4092-a7b8-58b9cf0616aa/image.png" width="200">


- Linked List, Stack Data structure

```c
Point* pushPoint(Point* head, int x, int y) { // (x, y)좌표를 저장하는 함수 (연결 리스트형 스택 자료구조 활용)
	Point* temp; // 임시 포인터 변수를 만듬
	temp = (Point*)malloc(sizeof(Point)); // 저장공간 할당

	temp->x = x; // x값 대입
	temp->y = y; // y값 대입
	temp->link = NULL; // 다음 연결 노드가 없다는 표시

... 생략 ..

	return head;

}
```

-base Canvas Function

```c
Stroke* paintCanvas(Stroke* head, IplImage* canvas, int mode) { // 논문상의 canvas 이미지에 색칠하는 함수
... 생략 ...
	}

```
- 곡선, 주변값들의 좌표값 저장
- 로컬상의 파일을 불러오기
<hr/>

### result

<img src="https://github.com/seunghyun0522/Painterly-Rendering/assets/75532258/4be15450-6de1-49b9-a1b2-562ac4847d87" width="180" weight="150" margin-right="100">
<img src="https://github.com/seunghyun0522/Painterly-Rendering/assets/75532258/5af1f7ad-6cc2-44c4-acc9-7b3efa50b4ec" width="180" weight="150">
<img src="https://github.com/seunghyun0522/Painterly-Rendering/assets/75532258/6cf32871-2129-478e-bc0b-60689436f090" width="180" weight="150">
<img src="https://github.com/seunghyun0522/Painterly-Rendering/assets/75532258/0976b89f-464b-422c-b8d3-700589704c42" width="180" weight="150">
<img src="https://github.com/seunghyun0522/Painterly-Rendering/assets/75532258/c9f0770e-43d7-4c53-a747-fe632d343124" width="180" weight="150">


[참고 논문 hertzmann](https://mrl.cs.nyu.edu/publications/painterly98/hertzmann-siggraph98.pdf)

<img width="702" alt="Hand-Gesture-Detective" src="https://user-images.githubusercontent.com/63290629/155256638-ec59c035-3ee3-4e96-baec-544488acaa0f.png">

<br>

# Hand-Gesture-Recognition

<br>

> ‘컴퓨터비전’ 수업 #1 과제 → Hand Gesture Detective

<br>

## ✅ 프로젝트 소개

- Skin Detection 기반으로 손 제스처를 인식
- 손가락의 개수를 세서 손 정보를 담을 수 있다.
- 손을 트랙킹해서 화면에 그림을 그리고 지울 수 있다.

<br>

## 📝 요구 사항 분석

- 어디에 있든지 손만 인식해야 한다.
- 손가락 개수를 세서 출력한다.
- 손의 중심을 마우스가 트랙킹할 수 있다.
- 주먹을 쥔 경우, 그림을 그릴 수 있다.
- 손가락 2개인 경우, 그림을 지울 수 있다.

<br>

## 💻 구현

- 손을 검출하기 위해 **피부색 영역**을 skin_area에 저장
- 피부 영역이 아닌 곳도 검출된다 → **열림 연산으로 배경 잡음 제거**
- skin_area와 배경 픽셀 사이 최소 거리를 행렬에 저장
- **손의 중심**은 위에서 구한 **행렬의 최댓값 좌표**로 설정하고, 거리의 최댓값을 반지름 변수에 저장하면 원을 그릴 수 있고, 이 원을 통해 손가락 개수를 카운트할 수 있다.
- 원의 외곽선을 따라 돌면서 마스크의 값이 **0에서 1로 바뀌는 지점**을 카운트했다. (손목도 카운트되므로 -1)
- 손을 감지할 수 있는 영역(ROI)을 따로 만들어서 손을 감지할 수 있도록 했다.

<br>


## ↪️ 진행 

<br>

<img width="589" alt="process" src="https://user-images.githubusercontent.com/63290629/155257029-33205982-7ad2-4ac1-ada4-580ef155725d.png">


<br>


## 🙋‍♀️ 역할  

- 손의 중심 계산, 손가락 개수 카운팅, 텍스트 출력
- 피부색 검출
- 피부색과 비슷한 색상 노이즈 제거 → open(열림 연산)
- 화면 절반을 ROI 영역으로 손을 인식할 수 있는 영역을 제한

<br>


## 💦 아쉬운 점  

손을 검출하기 위해 피부색상을 요소로 사용했기 때문에 만약 얼굴과 같이 손과 피부색이 동일한 것과 겹친 경우에는 손을 제대로 검출하지 못했다. 

<br>



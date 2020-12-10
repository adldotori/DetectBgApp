# DetectBgApp
모바일에서 전력 측정을 통해 백그라운드 앱의 실행여부를 탐지하는 프로그램이다. 

## EDA 
1초에 10번씩 30초 동안 측정하여 총 300개의 칼럼으로 생성  
총 1053개의 row

백그라운드 꺼져있는 경우 : 47%  
백그라운드 켜져있는 경우 : 53%  

## Feature Engineering
전력값들의 max, min, median, var, std 값 추가  
t=1,...,300 사이의 전력값 차이 추가  
1초의 평균 전력을 칼럼에 추가(10개의 columns마다 평균)   
t=1,...,300의  전력값 삭제  

## Modeling
RandomForestClassifier, KNeighborsClassifier, GaussianNB, rbfSVC  
위 4개의 모델 stacking

## Result
전력을 1초에 10번씩 30초동안 측정하면 89%의 확률로 백그라운드 앱의 실행여부 탐지 가능  
-> 내가 모든 앱을 다 껐음에도 백그라운드가 켜져있다면 해킹당한 것으로 의심할 수 있다  
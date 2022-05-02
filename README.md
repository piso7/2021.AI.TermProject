# 2021.AI.TermProject
Startup Success Prediction  
인공지능 미니챌린지 / 인공지능 디펜스게임  
2021 AI 수업에서 진행한 텀프로젝트입니다.  

AI Mini Challenge / AI Defense Game  
Term-Project from the AI lecture, 2021  

## 진행방법
[마감 10/31][1단계] 주제 선정  
[마감 11/14][2단계] 리더보드 제작 및 베이스라인 설정  
[마감 11/17][3단계] 리더보드 공격 (리더보드 제작자 제외)  
[마감 11/21][4단계] 리더보드 디팬스 (리더보드 제작자 만)  
[마감 11/28][5단계] 리더보드 재공격 (리더보드 제작자 제외) 

### ▶ 주제선정 : Topic selection  
전 세계적으로 스타트업은 폭발적으로 증가하고 있으며 제 주변에도 창업을 시작한 학우들이 많습니다.  
하지만 수많은 회사가 탄생하였듯이 사라지는 회사 또한 존재합니다.  
저는 역대 스타트업 회사들의 데이터를 통해 해당 스타트업의 성공 여부를 예측하는 모델을 만들고자 하였습니다.

The number of startups is exploding around the world, and there are many students around me who have started their own businesses.  
But just as many companies were born, there are companies that disappear.  
I wanted to create a model to predict the success of the startup based on data from previous startup companies.  

### ▶ 리더보드 제작 및 베이스라인 설정 : Kaggle leaderboard and baseline setup   
#### Dataset
<ul> 1. kaggle과 깃허브 등 다양한 source에서 데이터를 크롤링 </ul>
<ul> 2. 해당 데이터들에서 공통적인 columns를 갖도록 가공하여 Dataset을 마련 </ul>
<ul> 3. 예측에 이용할 Dataset 과 kaggle Evaluation Dataset은 8:2의 비율로 설정 </ul>

#### Dataset
<ul> 1. Crawling data from various sources such as kaggle and github </ul>
<ul> 2. Prepare Dataset by processing the data to have common columns </ul>
<ul> 3. Dataset to be used for prediction and kaggle Evaluation Dataset are set in a ratio of 8:2 </ul>

예측해야할 column은 'status' 이며 'closed', 'operating', 'acquired', 'ipo' 4가지 값이 존재합니다.  
'closed' 를 0, 나머지는 1로 매칭하여 제출하면 되겠습니다.

The column to predict is 'status', and there are 4 values: 'closed', 'operating', 'acquired', and 'ipo'.  
You have to submit by matching 'closed' with 0 and the rest with 1.

#### Baseline
<ul> Dataset을 이용하여 사용가능한 새로운 column을 추가하고 결측치를 처리 : Add new available columns using Dataset and handle missing values </ul>
<ul> Data normalization : StandardScaler(), Batch_size = 100 </ul>
<ul> Model : 5 layered DNN, 512 nodes, Activation function ReLU(), Initialize weights with Xavier_uniform </ul>
<ul> Optimizer: Adam, Learning_rate = 0.001 </ul>
<ul> loss function: CrossEntropyLoss() </ul>

위와 같은 설계를 통해 리더보드 상의 최고의 성능을 이끌어내고자 하였습니다.
Through the above design, i tried to bring out the best performance on the leaderboard.  

### ▶ 리더보드 디펜스 : Leaderboard Defence  
<ul> Baseline을 제작할때 의도치 않은 Data drop이 일어난것을 발견하고 데이터 수정 </ul>
<ul> Found that unintentional data drop occurred when creating the baseline and correct the data </ul>
<ul> 모델을 다중분류가 아닌 이중분류로 진행하도록 재설계 : Redesign the model to proceed with dual classification rather than multiclassification </ul>
<ul> 활성화함수를 Leaky_ReLU()로 변경, 파라미터 수정 : Change the activation function to Leaky_ReLU(), modify the parameters </ul>

![image](https://user-images.githubusercontent.com/62230550/147653832-16effd3f-5578-4fdc-9cbf-f906601eb791.png)

디펜스에 성공하였습니다.
Defense was successful.

### ▶ 링크 Link  
Raw data source:  
https://github.com/chenchenpan/Predict-Success-of-Startups/blob/master/companies.csv  
https://www.kaggle.com/ajitpasayat/startup-success-prediction-dataset

Term-project Kaggle Leaderboard:  
https://www.kaggle.com/c/2021ai-project-startup-success-prediction/overview

Final presentation video [문제 선정 / 데이터 가공 / 캐글 리더보드 제작 / 베이스 라인 구축]  
(Youtube): https://youtu.be/H1w7Rq6D77k

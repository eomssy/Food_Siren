# Food_Siren

### 왜 Food Siren 인가?
일반 가정에서 요리에 사용하는 다양한 '식품'의 유통기한을 관리하고, 식품의 유통기한이 임박하면 앱 이용자에게 이를 '알려준다'

### 프로젝트 개요 및 개발 필요성 및 목적
covid-19 사태 이후, 집 에서 직접 요리해먹는 '홈쿡' 트랜드가 확산됨에 따라 요리에 대해 관심을 가지는 사람이 증가하게 되었음, 집에 있는 자투리 시간에 간편하게 식품을 관리할 수 있는 어플리케이션을 개발하고 제공함으로써, 최근 증가한 '홈쿡커'를 비롯한 요리를 즐겨한느 사람들이 집 안의 식품을 좀 더 효율적으로 사용할 수 있는 방법을 제공하는 것의 목표. 



## 연구 내용 및 추진 방향

### 개발환경 (앱)

 
![2](https://user-images.githubusercontent.com/51026066/130903972-e88e58c7-3518-410a-b9cf-f2ebd87823c4.PNG)


### 개발환경 ( 백엔드)

![4](https://user-images.githubusercontent.com/51026066/130904228-f78f100c-a662-4d64-91a3-0cd4f7724a56.PNG)



### 라이브러리


#### Google에서 제공하는 바코드 스캔 오픈소스 Zxing 라이브러리 활용

![5](https://user-images.githubusercontent.com/51026066/130904674-acc72d16-30a1-418c-9153-c34dce77ab1c.PNG)



#### 푸쉬알림 및 App Widget Provider

![6](https://user-images.githubusercontent.com/51026066/130905076-e9fea25b-921d-4c78-b115-7d6e840fed05.PNG)


### 형상관리

![3](https://user-images.githubusercontent.com/51026066/130904116-ff0441c4-00c6-4b4e-bf3f-821786d6a75e.PNG)


### 데이터 연동 

'자취 3끼'라는 팀과 비슷한 주제로 어플리케이션 개발을 하고 있는 상황속, 자취 3끼 팀이 보유하고 있는 식품 관련 레시피 DB 정보에 대한 접근권한을 얻기 위해 연락을 취함. php 서버를 통해 Food Siren을 이용하는 고객이 자취 3끼에서 제공하는 '레시피 정보 제공'를 제공하도록 기능을 구현. 


![7](https://user-images.githubusercontent.com/51026066/130905680-71ac49b9-7676-4bad-92c3-88ef28ec1da5.PNG)


### 프로젝트 진행 과정

![8](https://user-images.githubusercontent.com/51026066/130906039-a8304c18-d3aa-465b-b2b3-405221e27235.PNG)




## 구현 내용 


### 패키지 구성
 
![9](https://user-images.githubusercontent.com/51026066/130906293-afe7d503-ceb2-4f31-9187-81bd79743066.PNG) 
- Model
- Util
- View
- ViewModel
- => MVVM 패턴을 사용하여 패키지를 구성.


#### model

![1](https://user-images.githubusercontent.com/51026066/131085586-3a887584-8a40-4060-ace0-27564458151d.PNG)

* data - 앱에서 사용되는 데이터
* database - 내부 DB


#### Util

* alarm - 푸시알람 기능
* etc - 웹 클롤링 등 부가 기능
* widget - 위젯 기능



#### view

![2](https://user-images.githubusercontent.com/51026066/131086050-a6f79bef-738d-43d6-ac03-3376c867b145.PNG)

* Activity - 앱을 구성하는 화면 



![3](https://user-images.githubusercontent.com/51026066/131086158-b1b989cc-4773-48bb-8e6b-fc64ec3b3c48.PNG)

* Adapter - 리스트 등의 View에 표시될 데이터를 연결담당
* Dialog - 앱에서 사용되는 다이얼로그 화면 
* Etc - 앱 인트로 등 기타화면


#### ViewModel


![4](https://user-images.githubusercontent.com/51026066/131086274-87897a38-d29f-4ae7-9589-90a9265129d0.PNG)


* Data 와 View 사이에서 데이터의 이동을 담당.



## 클래스 명세 


#### Data
 
 
* Category - 카테고리의 데이터타입이 정의되고, 액티비티 내에 사용될 다양한 함수들이
정의되어있는 클래스. Food - 식품의 데이터타입이 정의되어있다. 그리고 다양한 액티비티 내에 사용되는 유
통기한과 관련된 시간함수들이 정의되어있는 클래스이다. Recipe - 레시피 액티비티내에서 사용되는 레시피들의 데이터 타입과 함수들이 정의되
어 있는 클래스.
 
 
 

#### DataBase
 
 
* FoodSirenDB - 앱이 가지고있는 내부 데이터베이스 정의를 돕는 클래스이다. 싱글톤
패턴으로 정의되어 중복된 데이터베이스가 정의되지 않도록 설정하였다. 

#### Alarm


* AlarmReceiver - FoodAdapter내에서 알람 ON/OFF 중 ON을 누를 경우 실질적인
알람의 등록을 해주는 클래스이다. 이 클래스는 EditTimeActivity에서 알림 시간을 수정
할때에도 사용된다.


#### Widget


* WidgetView - 위젯의 리스트뷰를 형성시키고 MyRemoteViewsFactory의 정보들을 리
스트뷰에 담아준다. 
* WidgetFactory- 위젯 리스트내에 들어갈 하나의 식품열을 정의해놓은 클래스이며 식품
열을 누를때에 매니지 화면으로 넘어가도록 한다. 
* WidgetService - MyRemoteViewsFactory의 객체 생성을 돕는 클래스이다.


#### Acitivty


* BarcodeActivity- 앱에서 사용자가 zxing 라이브러리 기반의 스캔을 시작하였을때, 해
당되는 상품명과 이미지를 외부에서 받아오기 위한 액티비티이다. JsoupAsyncTask 기반
의 크롤링 방법을 활용해서 외부 데이터를 보다 효율적으로 끌어오도록 구성하였다. 

* EditTimeActivity - 메인에서 drawer를 열었을 때 실행되는 activity로 푸쉬알람 받을
시간을 timepicker로 지정하여 원하는 시간에 푸시알람이 사용자 앱에서 울리도록 구성

* EnrollActivity - 상품을 등록하기 위한 activity로, 해당 상품의 사진을 직접 촬영하거
나, 앨범에 있는 사진을 불러와 등록 할 수 있으며, zxing라이브러리기반의 바코드 스캐
너를 구성하여 앱에서 스캔한 상품정보를 외부 데이터에서 끌어와 보다 효율적으로 상품
정보를 등록할 수 있다. 또한 datepicker를 활용하여 사용자가 보다 쉽게 등록일을 지정
하고 등록할 수 있도록 구성하였다.

* MainActivity - Enroll 과 Manage Activity로 연결을 해주는 액티비티로, 주로 두개의
액티비티로 연결을 해주는 역할을 수행함. 또한 드로어뷰를 제공하여 드로어를 열었을때
editTimeActivity 화면으로 인텐트 되도록 구성을 했다.유통기한이 지난 상품이 db에 등
록되어 있으면 메인에 처음 들어왔을때, 해당 상품들을 일괄 삭제 해주는 다이얼로그 창
을 띄어주고, 해당 상품들을 일괄 삭제해주는 역할을 수행하는 activity이다.

* ManageActivity - Enroll에서 등록한 식자재를 관리해주는 Activity이다. 사용자가 등
록한 상품을 카테고리와 기한에 맞게 일괄 정렬하여 보여주도록 구성을 하였으며, 기본적
으로 검색, 수정, 삭제, 푸쉬알람 활성화, 유통기한이 지남에 따른 progress bar 변화, Tip 정보를 제공하는 등 사용자가 보다 효율적으로 식자재를 관리할 수 있도록 도와주는
Activity이다. 

* PhotoActivity - enroll Activity에서 이미지를 활용하여 상품등록 할때 사용하기 위한
Activity이다. 앱자체에서 카메라 기능을 제공하여 사용자가 상품 이미지를 등록할때 직
접 촬영하여 사용할 수 있는 역할을 수행하며, 앨범에 이미 저장되어 있는 사진을 가져와
서 상품 이미지를 등록할 수 있도록 구성하였다. 안드로이드에서 이미지를 빠르고 효율적
으로 불러올 수 있는 Glide 라이브러리를 활용하여 해당 Activity를 구성하였다. 

* RecipeActivity - 4조 자취새끼의 외부 DB 서버에서 레시피 정보를 받아오고 연결 해
주기 위한 Activity로 외부 DB서버에 접근하여 데이터 값을 Json형식으로 받아오고 받아
온 정보를 앱에서 띄어주는 역할을 수행하는 Activity이다.

* RecipeInfoActivity - RecipeActivity에서 받아온 레시피 정보를 사용자가 보기 편하게
띄어주는 역할을 수행하는 Activity이다.

* SplashActivity - 앱을 맨처음 실행했을때 사용자에게 앱에 대한 간단한 소개를 해주
며, db에서 실질적인 date를 가져오는 역할을 수행하는 activity이다.

* TipActivity - ManageActivity에서 사용자가 등록한 상품에 대한 다른 부가적인 정보
를 알고 싶을 때, 다양한 인터페이스를 제공해주는 Activity로, 해당 식자재에 대한 보관
방법과 배출 방법, 관리에 대한 정보를 인터넷 검색을 통해서 자동으로 제공해주고, 앱에
등록한 상품을 구매 할 수 있는 구매처 정보에 대한 정보를 제공한다. 추가로 상품과 연
관된 레시피 정보를 제공하는 역할을 수행한다.

#### Adapter


* FoodAdapter - 식품관리 화면에서 리스트내에 들어갈 하나의 식품열에 대해 식품의
이미지, 이름, 유통기한 남은 일자, 식품 개수와 같은 정보들을 보여준다. 또한 식품의 유통기한이 얼마 남지않았음을 알려주는 알림을 AlarmReceiver에 전달해주
는 기능을 담당한다.

* RecipeAdapter - TipActivity를 통해 원하는 재료가 포함된 레시피를 리스트형태로 보
여주고 리스트내에서 레시피 이름과 정보를 하나의 칸으로 확인할 수 있다.


#### Dialog


* AddCategoryDialog - 카테고리 추가를 도와주는 다이얼로그. 

* CategoryDialogClickListener - AddCategoryDialog와 DelCategoryDialog내에 클
릭 이벤트를 돕는 인터페이스.

* DelCategoryDialog - 특정 카테고리 삭제를 도와주는 다이얼로그. 

* MenuDialog - 바코드를 인식할 수 없는 특정 식품들의 유통기한을 현재날짜를 기준으
로 자동으로 지정해주는 다이얼로그. 

* MenuDialogClickListener - MenuDialog내에 클릭 이벤트를 돕는 인터페이스. 

* ModifyDialog - ManageActivity에서 수정 버튼을 눌렀을때 수행되는 Activity로, 안드
로이드에서 기본적으로 제공하는 dialog 방식을 사용한것이 아닌, activity가 dialog 처럼
보이도록 커스터마이징을하여, 사용자가 특정 상품에 대한 정보를 수정하고 싶을 때 수정
기능을 제공하는 Activity이다. 기본적으로 상품명과 수량, 카테고리를 수정할 수 있으며, 등록일과 유통기한 또한 datePicker를 활용하여 보다 편하게 수정할 수 있도록 구성했
다.

#### Viewmodel

* CategoryViewModel, FoodViewModel - Activity가 직접 DB에 접근해서 Data를 사
용하는 것은 Activity와 같은 View계층이 맡는 일이 아니다. 따라서 이를 ViewModel이
라는 클래스를 통해 맡아서 처리하여 데이터를 사용하도록 한다. 이때 데이터는 다양한
쿼리문들(Update, Delete등등)을 통해 사용된다. 추가로 AppDatabase를 활용해서 데이
터베이스를 생성하도록 한다. 

* CategoryDao, FoodDao - 데이터베이스로의 접근을 도와주는 인터페이스.


#### etc

* FoodSirenIntro - github에서 제공하는 Appintro open source library를 활용하여
구성하였고, Fragment 기반의 화면전환이 slide 뷰 형식 일어난다. 사용자가 앱을 맨처
음 빌드 or 설치 했을때, 앱의 간단한 기능과 앱에 대한 설명을 보기 쉽게 알아볼 수 있
도록 화면 구성을 하였으며, Appintro는 Activity는 앱을 처음 실행 하였을때만 제공되어
야 하는 일회성 activity이기 때문에 sharedPreferences를 활용하여 일회성으로 한번만
activity가 출력되도록 구성하였다. 

* SSLConnector - 앱에서 바코드 스캔을 진행할때, 크롤링을 기반으로 외부에서 데이터
를 가져오기 때문에, 특정 웹 사이트에서 데이터를 가져올때 암호화된 인증키를 요구하는
사이트들이 있다. 그러한 암호화된 문제를 해결하고 연결을 쉽게하기 위하여 해당
activity를 구성하여 크롤링을 해올 때 문제 없이 받아오도록 구성을 하였다. 






## 구현화면


#### APP Intro - 추후에 이미지 캡쳐해서 삽입- 



#### Main


![7](https://user-images.githubusercontent.com/51026066/131087569-085d122f-9ab6-4728-beda-5fce7b254f0c.PNG)



#### 식품등록


![5](https://user-images.githubusercontent.com/51026066/131087628-98f5691c-72e0-4ef3-94f7-59065222af84.PNG)

미리 등록해둔 식품 목록



![6](https://user-images.githubusercontent.com/51026066/131087693-64717cc4-2889-46ff-acc0-35a92e9f3c3c.PNG)

상품등록 

#### 상품 등록, 삭제, 수정, 다이얼로그, 부분 캡쳐해서 넣기 


#### 식품별 팁 


![9](https://user-images.githubusercontent.com/51026066/131087809-12a2e142-b055-4f43-8363-71c942437624.PNG)


##### 자취3끼랑 연동한 화면 캡쳐해서 넣기 


#### 위젯 


![10](https://user-images.githubusercontent.com/51026066/131087987-02add526-05f6-405b-b8af-b865f86c9413.PNG)


#### 푸시알람 넣기 





#### 구현 기능 

-식품의 바코드를 읽어 식품의 이름과 사진을 자동으로 불러오는 바코드 스캔

-바코드가 없는 신선 식품의 유통기한을 추천해주는 신선식품 간편등록

-보관 중인 식품을 한 눈에 확인할 수 있는 식품 관리

-식품의 남은 유통기한을 자동으로 체크하여 알려주는 알림 기능

-식품을 이용하여 만들 수 있는 다양한 요리의 레시피 정보 제공

-식품에 대한 다양한 부가정보를 웹 검색을 통해 확인할 수 있는 빠른 웹 검색

-앱을 실행하지 않고도 식품의 유통기한을 확인할 수 있는 위젯 기능



## 개발하며 느낀점 

### 1. 코드 중복


프로젝트를 진행하면서 정기적으로 코드의 일관성을 유지하기 위해 코드 리팩토링을 진행했음에도 불구하고 개발 종료 기간이 다가오고 점차 많은 기능들이 생겨나면서 몇 가지 코드가 중복되어 코드의 통일성이 저하되는 문제가 있었다.


### 2. 단순한 화면 이동


FoodSiren은 Activity(하나의 화면)간의 이동을 기반으로 만든 프로그램이기 때문에, 특정 버튼을 눌러 화면을 이동하고 뒤로가기 버튼을 통해 나오는 단순한 형태의 화면 이동만을 지원한다. 따라서 사용자가 특정 화면으로 이동하려면 꼭 주어진 절차를 따라야 한다는 단점이 생겼다. 이러한 단점을 해결할 수 있는 Fragment 방식이 있지만, 앱을 설계할 당시에는 이러한 화면 이동이 단점이 될 것이라 예상하지 못하였기 때문에 Activity 를 통한 화면 이동을 사용했다. Fragment 기반으로 앱을 만들었다면 훨씬 앱 개발이 수월했을 것이라 생각한다. 

### 3. 앱 설정 기능 일부 미제공


기존에 프로젝트를 계획했을 때는 앱에서 제공하는 기능에 대한 구현을 마무리한 후에 앱 설정 기능을 만들어 제공할 예정이었으나, 개발 기간이 생각보다 오래 걸려 해당 사항을 프로그램에서 제외시키고, 사용자에게 꼭 필요하다고 생각하는 설정만 따로 제공하였다.


### 4. 데이터 백업 및 가져오기 미제공


앱에서 사용되는 데이터는 모두 사용자의 메모리에 저장되는 내부 DB 형식이기 때문에, 앱이 삭제되거나 앱에 저장된 데이터를 지울 경우 해당 데이터를 복구할 수 없다.
이에 대한 해결 방법으로 많은 앱이 데이터 백업 및 가져오기 기능을 제공하는데, 시간적인 여유가 부족하여 해당 기능을 구현하지 못하였다.
 
 
 ## 부족했던 점 
 
 ### 1. 작업에 대한 불확실한 이해


프로젝트 초반 작업 계획에 대해 팀원이 서로 이해한 바가 달라 의도하지 않은 결과물을 만들어오는 일이 발생하였다. 이후 서로가 확실히 계획을 이해했는지 확인하고, 작업을 시작하기 전에 작업사항을 정리함으로써 이러한 일이 발생하지 않도록 방지하는 과정을 매번 진행하였다.
 

### 2. 주관적인 의견에 대한 결핍


5인이 함께 프로젝트를 진행하다 보니 어느 새 팀원들 모두 개인적인 의견을 내는 것을 꺼려하고, 사소한 것 마저도 모두의 의견을 참고해야만 일이 진행되는 경우가 있었다. 따라서 프로젝트를 진행하는 데 꼭 모두의 의견이 필요한 것이 아닌 일에 대해서는 개인적인 판단을 바탕으로 일을 진행하고 후에 피드백을 받는 방식으로 하니, 절차가 간단해지고, 참신하고 다양한 아이디어를 바탕으로 앱을 만들 수 있었다.

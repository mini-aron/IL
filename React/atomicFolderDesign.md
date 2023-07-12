# atomic folder design
원자단위로 분해하는거처럼 컴포넌트나 기능을 쪼개고 쪼개서  
컴포넌트의 재사용성과 유지보수성을 높이기 위한 방법중 하나다!!

## components 내부 폴더 구조!

```
src
 └─ components
    ├─ atomics
        ├─ Button
        ├─ TextField
        └─ Icon
    ├─ molecules
        ├─ SearchForm
        ├─ LoginForm
        └─ Card
    ├─ organisms
        ├─ Header
        ├─ Sidebar
        └─ CardList
    ├─ templates
        ├─ HomePage
        ├─ BlogPage
        └─ ProductDetailPage
    └─ pages
        ├─ MainPage
        ├─ UserProfilePage
        └─ SettingsPage
```
1. ### Atoms
원자같이 단순한 UI요소로, 다른 컴포넌트를 구성하는데 사용된다.  
예를 들어 버튼, 텍스트필드, 아이콘, 레이블등이 있당  
2. ### Molecules  
원자 컴포넌트를 조합해 더 복잡한 컴포넌트로 구성한다.  
예를들어 검색폼, 로그인폼, 카드등이 있당.
3. ### Organisms
분자 컴포넌트들을 조합하여 더 큰 기능적인 블록으로 구성한다.  
예를들어 header,sidebar,cardlist등이 있당.
4. ### Templates 
여러개의 유기체 컴포넌트들을 배치해 페이지 전체의 레이아웃을 구성한다.  
예를들어 홈페이지, 블로그 페이지, 제품 디테일 페이지 등이 있다.  
5. ### Pages  
실제 프로젝트에서 사용되는 개별페이지를 나타낸다.  
예를들어 메인페이지, 사용자 프로필 페지, 설정 페이지 등이 있당.
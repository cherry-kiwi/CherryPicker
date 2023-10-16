https://youtu.be/gFpmJtO0NT4?si=XK0484e2Xwvh5PKD
## City Builders
### 세팅하기
1. 하이라키 창 > 2D Object > Isometric Tilemap 에서 Grid 생성
2. Grid 오브젝트의 자식 오브젝트인 Tilemap 개체를 하나 더 복사하여 기본 타일맵(Main Tilemap), 표시용 임시 타일맵(Temp Tilemap - 솔팅 레이어 "Background"로 지정, Background 레이어는 Default보다 위에 있게 드래그) 두 개를 생성
3. 두 자식 오브젝트의 Tilemap renderer 컴포넌트의 Sorting Layer을 Background로 지정, Temp Tilemap의 Order in Layer은 1로 지정
4. 건물을 생성할 버튼 하나 생성
5. House 1 오브젝트명을 "Sprite"로 변경 후, "House Prefab"라는 이름으로 지정한 빈 오브젝트의 자식으로 상속시키고 프리팹화함
6. 흰색: 사용 가능한 영영 / 녹색: 집 영역 / 적색: 배치 불가 영역 타일 세팅
### 코딩하기
#### 📜**GridBuildingSystem**
- Grid 오브젝트에 배치
- 싱글톤 패턴 -> 이에 대한 참조 만들어야함
	- ex) public static GridBuildingSystem instance;

- Unity Methods
	- Awake에서 instance = this로 초기화
	- Start
	- Update

- Tilemap Management
	- 타일맵에서 타일을 가져오고 설정하는데 사용

- Building Placemet
	- 건물 배치 담당

- 그리드 레이아웃 및 타일맵에 대한 참조 만들기
	- GridLayout gridLayout -> Grid
	- Tilemap MainTilemap -> main Tilemap
	- Tilemap TempTilemap -> temp Tilemap

- TileType이라는 열거형 생성
	- Empty
	- White
	- Green
	- Red

- TileType이라는 [[딕셔너리]] 생성 후,
	-     private static Dictionary<TileType, TileBase> tileBases = new Dictionary<TileType, TileBase>();
	- TileBase: https://docs.unity3d.com/kr/2021.3/Manual/Tilemap-ScriptableTiles-TileBase.html
- start에서 초기화

- 세 개의 메서드 따라치기..

- 건물에 대한 참조
	- 

#### 📜**Building**
- House Prefab에 배치
- Build Methods
	- 영역에 따라 배열을 생성하는 타
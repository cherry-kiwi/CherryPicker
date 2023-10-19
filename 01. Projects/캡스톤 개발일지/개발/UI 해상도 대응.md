- Canvas - Render Mode
	- Screen Space - Overaly -> Camera 로 변경하여 해당 카메라에만 렌더되어 보이게
- Projection 값을 Orthographic으로 설정
- Canvas Scaler
- UI Scale Mode: Scale With Screen Size
- Reference Resolution: 원하는 기준 해상도 (1080x1920)

>[!note] 
>다른 해상도에서 동일한 비율의 UI 만들기

## 해상도 고정시키기
### Canvas Scalar 컴포넌트
- **Constant Pixel Size**: UI 요소가 화면 크기에 관계없이 동일한 픽셀 크기로 유지
- **Scale With Screen Size**: 스크린이 커질수록 UI도 커짐
- **Constant Physical Size**: UI 크기 계속 유지

### UI Scale Mode
- **Scale With Screen Size**
- **Reference Resolution** - 1920 * 1080 
- **Screen Match Mode**
	- Match Width Or Height: 기준이 되는 해상도의 가로 or 세로 중 하나를 기준으로 해서 비율을 유지한 채 **확장 or 축소**
	- Expand: 캔버스 크기가 Reference Resolution에 설정한 값보다 더 작아지지 않도록 캔버스 영역을 수평 또는 수직으로 확장
	- Shrink: 캔버스 크기가 Reference Resolution에 설정한 값보다 커지지 않도록 캔버스 영역을 수평 또는 수직으로 잘라냄
	- Match Width of Height
		- Match 값 0 = Expand -> 가로뷰 GOOD
		- Match 값 1 = Shrink -> 세로뷰 GOOD
- Match: 1
## 게임 내 해상도 고정(SetResolution 함수)
### 해상도를 특정 해상도로 고정 **(비추!!)**
Screen.SetResolution(int width, int height, bool fullscreen);
### 기기 비율에 맞게 해상도 고정
Screen.SetResolution(Screen.width, Screen.width * int SetWidth/int SetHeight, bool fullscreen);

ex) 16:9 비율일 시, Screen.SetResolution( Screen.width, (Screen.width * 16) / 9 , true);
- Start() 함수나 Awake() 함수에 작성하여 빈 오브젝트에 삽입
- 화면을 고정하고 싶은 모든 씬에 작성
## 아이폰 노치 대응 (Safe Area)
- SafeArea 
```
using UnityEngine;

public class SafeArea : MonoBehaviour
{
    RectTransform _rectTransform;
    Rect _safeArea;
    Vector2 _minAnchor;
    Vector2 _maxAnchor;

    void Awake()
    {
        _rectTransform = GetComponent<RectTransform>();
        _safeArea = Screen.safeArea;
        _minAnchor = _safeArea.position;
        _maxAnchor = _minAnchor + _safeArea.size;

        _minAnchor.x /= Screen.width;
        _minAnchor.y /= Screen.height;
        _maxAnchor.x /= Screen.width;
        _maxAnchor.y /= Screen.height;

        _rectTransform.anchorMin = _minAnchor;
        _rectTransform.anchorMax = _maxAnchor;
    }
}
```
1. Canvas 하위에 빈 오브젝트를 하나 만든 뒤, 설정을 해주고
2. Canvas 요소들을 자식으로 보낸다


참고 글
https://tkablog.tistory.com/entry/UnityGUI-%EB%AA%A8%EB%B0%94%EC%9D%BC-%ED%95%B4%EC%83%81%EB%8F%84-%EB%8C%80%EC%9D%91
https://giseung.tistory.com/19
https://blog.naver.com/semgames/222990580015
https://blog.naver.com/semgames/222043362699
https://solution94.tistory.com/76
https://young-94.tistory.com/92
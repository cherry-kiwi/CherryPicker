- Canvas - Render Mode
	- Screen Space - Overaly -> Camera 로 변경하여 해당 카메라에만 렌더되어 보이게
- Projection 값을 Orthographic으로 설정
- Canvas Scaler
- UI Scale Mode: Scale With Screen Size
- Reference Resolution: 원하는 기준 해상도 (1080x1920)

>[!note] 
>다른 해상도에서 동일한 비율의 UI 만들기

### Canvas Scalar 컴포넌트
- **Constant Pixel Size**: UI 요소가 화면 크기에 관계없이 동일한 픽셀 크기로 유지
- **Scale With Screen Size**: 화면이 커질수록 UI 요소 크기도 커짐
- **Constant Physical Size**: 화면 크기와 해상도에 관계없이 UI 요소가 동일한 물리적인 크기로 유지

### UI Scale Mode
- **Scale With Screen Size**
- Reference Resolution - 1920 * 1080 
- Screen Match Mode - Match Width Or Height
- Match: 1

참고 글
https://tkablog.tistory.com/entry/UnityGUI-%EB%AA%A8%EB%B0%94%EC%9D%BC-%ED%95%B4%EC%83%81%EB%8F%84-%EB%8C%80%EC%9D%91
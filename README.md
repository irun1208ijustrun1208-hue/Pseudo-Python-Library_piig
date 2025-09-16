# Pseudo-Python-Library_piig
파이썬 모듈인데 좀 개같음
piig

piig는 Pygame-CE 기반 UI/유틸리티 모듈이다. 리듬게임이나 2D/3D 프로토타입, 툴 제작에 필요한 폰트/테마/위젯/카메라/리듬 시계 기능을 모아 제공한다.

주요 기능

UI 위젯

label, button, textbox, slider, dropdown 등 기본 컨트롤 제공

포커스·키보드 입력·마우스 상호작용 지원

테마 시스템과 연동

폰트 관리 (FontManager)

한글 포함 다국어 폰트 후보 리스트 내장

사용 가능 폰트를 자동 선택

테마 시스템 (ThemeManager)

색상 팔레트 기반 테마 정의

UI 전체에 일괄 적용 가능

카메라 (Camera)

화면 이동·확대/축소 제어

줌 레벨 제한, 스무딩 지원

리듬 시계 (RhythmClock)

BPM 기반 타이밍 계산

오프셋·레이턴시 보정

재생/일시정지/시크/퀀타이즈 기능

리소스 로딩

assets.image(path) → 자동 캐싱, convert_alpha 예외 안전

assets.sound(path) → Pygame mixer 활용

키/입력 관리 (Keys)

사용자 키바인딩 저장·불러오기

중복 키 경고 및 예외 처리

스프라이트 관리 (Sprite)

기본 이미지/애니메이션 처리

설치 및 실행

    pip install pygame-ce
    git clone <repo_url>
    cd piig
    python -m examples.ui_showcase

예제

    import pygame
    from piig import UI, ThemeManager
    
    pygame.init()
    screen = pygame.display.set_mode((960,540))
    clock = pygame.time.Clock()
    ui = UI()
    theme = ThemeManager()
    
    running=True
    while running:
        events = pygame.event.get()
        for e in events:
            if e.type==pygame.QUIT: running=False
    
        screen.fill((18,18,20))
        ui.begin(screen, events)
        if ui.button(20,60,160,36,"Apply Theme"):
            theme.apply(ui)
        ui.end()
    
        pygame.display.flip()
        clock.tick(60)
    
    pygame.quit()


장점

Pygame-CE 기반 → 설치 간단, 범용성 높음

UI/테마/폰트/리듬 시계까지 한 패키지에서 해결

예제 포함, 바로 실행 가능

현재 한계

고급 IME(한글 조합) 처리 미흡 → TEXTEDITING 이벤트 개선 필요

포커스 이동(Tab/Shift+Tab) 제한적

게임패드 입력 지원 없음

문서화 및 자동 테스트 부족

앞으로 개선할 점

IME 완전 대응 및 다국어 입력 강화

접근성(포커스 순환, 키보드 내비게이션) 향상

게임패드·터치 입력 지원

UI 컴포넌트 확장 (체크박스, 라디오버튼, 스크롤 등)

샘플·테스트 추가 및 문서 보강

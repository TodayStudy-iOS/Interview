## 07. Debugging
### Xcode에서 디버깅 시 자주 사용하는 기능은 무엇인가요?
- Breakpoint
    : 프로그램의 문제가 되는 지점을 찾아 멈추고, 여러가지 조건을 바꾸어 보며 테스트.
- LLDB Console
    : LLVM의 Debugger Component를 개발하는 서브 프로젝트.
    : Low-Level 컨트롤이 가능한 모듈들로 이루어져 있어, 기계어에 가까운 영역까지 디버깅 가능.
    : [LLDB Debugger LINK](https://lldb.llvm.org/index.html)
- View Debugging - hierachy
    : UI Debugging, 뷰 계층 구조를 3D로 시각화.
    : Autolayout 제약 문제 해결.
    : 뷰의 크기, 위치, 숨김 상태 확인.
- Debug Navigator
    : CPU, Memory, 네트워크 등의 리소스 사용량을 실시간으로 확인. 
- Instruments
    : 앱의 성능, 메모리, 네트워크 사용량 분석
    : Time Profiler - hangs 표시, 성능 병목 발견.
    : SwiftUI View Body - 뷰 본문 실행 성능 체크.
    : [WWDC LINK](https://developer.apple.com/videos/play/wwdc2023/10248/)
- Memory Debugging
    : Memory Graph Debugger
    : 메모리 상태 시각적으로 확인
    : 메모리 LEAKS 탐지
    : 순환 참조 문제 확인
- Logging
    : NSLog, print
    : os_log

### 중단점(Breakpoint)의 종류와 활용 방법을 설명해주세요. 
- Regular Breakpoint
    : 코드 특정 줄에 설정하여 실행을 멈춤.
- Conditional Breakpoint
    : 특정 조건이 만족될 때만 실행을 멈춤.
    : Edit Breakpoint
- Exception Breakpoint
    : 예외 발생 시 실행을 멈춤. 
    : 런타임 에러 추적하는 데 유용.
    : 강제 언래핑으로 인한 crash debugging.
- Symbolic Breakpoint
    : 특정 메서드에서 실행을 멈춤.
    : 외부 라이브러리 메서드 디버깅.
- Global Breakpoint
    : 런타임 시작과 종료 등 앱의 특정 이벤트에서 실행을 멈춤.
    : 앱 실행 직후 상태 확인.
    : 앱 종료 직전 메모리 상태 확인.
- Action Breakpoint
    : 코드 실행을 멈추지 않고 로그를 출력하거나 스크립트를 실행.
    : 특정 이벤트 발생 시 로그 출력 혹은 스크립트 실행.

### LLDB 콘솔에서 유용한 명령어는 어떤 것이 있나요?
값을 출력하는 po, p, 단계를 확인하는 n, s, 실행 위치를 확인하는 bt 등을 유용하게 사용합니다. 
- po
    : 특정 객체나 변수의 값 출력
- p
    : 간단한 데이터 타입 값 출력
- n
    : 현재 break 걸려있는 지점에서 바로 다음 Statement로 Step Over
- s
    : 다음 Statement가 Function Call인 경우 Debugger를 해당 한수 내부에 위치한 시작 지점으로 이동 (Step in).
    - Debug Symbol이 없는 함수의 경우는 Step in을 무시하고 프로그램이 진행됨.
    - Symbol: Method, Variable, Class 등 기계가 아닌 사람의 눈으로 알아볼 수 있는 Source Code를 이루는 작은 단위.
- bt
    : 호출 스택을 출력하여 현재 실행 위치 확인

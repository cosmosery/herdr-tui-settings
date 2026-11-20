# Herdr TUI 설정

`config.toml`은 `~/.config/herdr/config.toml`에 복사해서 사용합니다.

접두키는 `Ctrl+B`입니다. 접두키를 누르고 손을 뗀 뒤 다음 키를 입력합니다.

| 키 | 동작 |
| --- | --- |
| `h/j/k/l` | Pane 포커스 이동 |
| `Ctrl+h/j/k/l` | 왼쪽/아래/위/오른쪽 Pane과 위치 교환 |
| `H/J/K/L` | Pane 크기 조절 |
| `p/n` | 이전/다음 탭 |

`Ctrl+h/l`은 Pane 위치 교환에 사용하므로 이전/다음 탭 단축키에서는 제외했습니다.

`navigator-hl.patch`는 Herdr v0.9.5 소스에 적용합니다. `Ctrl+B`를 누른 뒤 `g`로 이동할 화면을 열면 `h`는 이전 머신, `l`은 다음 머신 이름을 선택합니다. `Enter`로 선택한 머신을 엽니다.

빌드에는 Rust와 Zig 0.16.0이 필요합니다. 다른 Zig 버전이 기본으로 설치되어 있으면 `ZIG` 환경 변수로 0.16.0 실행 파일을 지정합니다. [Zig 공식 배포 목록](https://ziglang.org/download/#release-history)

```sh
# Herdr v0.9.5 소스 디렉터리에서 실행
 git apply /path/to/herdr-tui-settings/navigator-hl.patch
 cargo build --locked --release --bin herdr
 install -m 755 target/release/herdr ~/.local/bin/herdr
```

`~/.local/bin`이 `PATH`에서 기본 Herdr 설치 경로보다 앞에 있어야 합니다. 이미 열린 TUI는 `Ctrl+B`를 누른 뒤 `d`로 분리하고 `herdr`를 다시 실행하면 기존 세션에 연결됩니다.

`endpoints.json`은 머신 목록입니다. 복원할 때 `~/.local/state/herdr/client/endpoints.json`에 복사합니다. 별도 머신이 이미 등록되어 있으면 기존 파일을 먼저 백업하세요. SSH 비밀번호와 키는 별도로 관리합니다.

현재 접속 대상은 `home`, `dorm-ubuntu`, `dorm-windows`, `dorm` SSH 별칭입니다. 다른 컴퓨터에 복원할 때는 `~/.ssh/config`에도 해당 별칭을 설정해야 합니다.

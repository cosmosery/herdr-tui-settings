# Herdr TUI 설정

`config.toml`은 `~/.config/herdr/config.toml`에 복사해서 사용합니다.

`navigator-hl.patch`는 Herdr v0.9.5 소스에 적용합니다. `Ctrl+B`를 누른 뒤 `g`로 이동할 화면을 열면 `h`와 `l`이 왼쪽·오른쪽 화살표처럼 동작합니다.

```sh
# Herdr v0.9.5 소스 디렉터리에서 실행
 git apply /path/to/herdr-tui-settings/navigator-hl.patch
 cargo build --locked --release --bin herdr
 install -m 755 target/release/herdr ~/.local/bin/herdr
```

`~/.local/bin`이 `PATH`에서 기본 Herdr 설치 경로보다 앞에 있어야 합니다. 이미 열린 TUI는 `Ctrl+B`를 누른 뒤 `d`로 분리하고 `herdr`를 다시 실행하면 기존 세션에 연결됩니다.

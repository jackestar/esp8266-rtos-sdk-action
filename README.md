# ESP8266 RTOS SDK Build - GitHub Action

This repository provides a composite GitHub Action that installs the ESP8266 RTOS SDK and builds firmware using `make` on Ubuntu runners. Using only the [Espressif repository](https://github.com/espressif/ESP8266_RTOS_SDK) for toolchain and SDK installation, making use of the repository installation scripts

## Usage

Add a step in your workflow to call this action (uses the repo or a published action name):

```yaml
uses: jackestar/esp8266-rtos-sdk-action@V0
with:
  sdk-ref: 'master'        # optional
  install-deps: 'true'     # optional
  make-target: ''          # optional, e.g. 'clean' or 'flash'
```

## Inputs

- `sdk-ref` (string) - git ref to checkout for the ESP8266_RTOS_SDK. Default: `master`.
- `install-deps` (string) - whether to run `apt-get` to install required system packages. Set to `false` if you use a self-hosted runner with dependencies preinstalled. Default: `true`.
- `make-target` (string) - optional make target to invoke. Default: blank (runs `make`).

## Example

See `.github/workflows/example.yml` for a simple example that runs on `ubuntu-latest` and uploads build artifacts.

## Notes

- This action executes the SDK's `install.sh` and sources `export.sh`. The SDK installer may modify the runner environment and download additional toolchains.
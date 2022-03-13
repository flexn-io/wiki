# Tizen Watch

## Prerequisites

Before you begin make sure that you have your [environment set up](environment-setup-guide.md) and have the following tools:

- Java 1.8.0_275 version
- Tizen Studio 4.1 version

## Running the App on Device

> Since rnv run command is giving us problems mentioned above, for now running on device involves a bit more manual work.
>
> Steps described below requires [Tizen CLI](https://developer.tizen.org/ko/development/tizen-studio/web-tools/cli?langredirect=1).

1. Build the app. The build will be located at `platformBuilds/harness_tizenwatch/project/build`.

    ```console
    npx rnv build -p tizenwatch -s release
    ```

2. Connect your device via Tizen's Package Manager. Detailed instructions can be found [here](https://developer.samsung.com/sdp/blog/en-us/2021/04/12/remote-device-manager-an-easy-way-to-launch-your-application-with-tizen-studio).
3. Create **SAMSUNG** certificate in Tizen's Certificate Manager. The name of certificate will be used in the next step, right after `-s` option, so be sure to remember it. In this case, **_Flexn_** is used.
4. Open build folder in your terminal

    ```console
    cd ./platformBuilds/harness_tizenwatch/project/build
    ```

5. Package and sign your build

    ```console
    tizen package -t wgt -s Flexn -- ./
    ```

6. If you had _Test-Harness_ app installed previously, uninstall it first

    ```console
    tizen uninstall -p cHIP2fIRQZ -t <TARGET_DEVICE_NAME>
    ```

7. Install the _Test-Harness_ app

    ```console
    tizen install -- ./ -n Harness.wgt -t <TARGET_DEVICE_NAME>
    ```

8. Run the app on remote device

    ```console
    tizen run -p cHIP2fIRQZ -t <TARGET_DEVICE_NAME>
    ```

## Found `rnv` issues

1. `rnv` does not find connected device when executing `npx rnv run -p tizenwatch -d` command ([docs reference](https://renative.org/docs/0.30/platform-tizenwatch#run)).
2. Tizen Studio throws certificate error when trying to run generated code by `rnv` directly from Tizen studio.

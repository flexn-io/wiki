# Apple CarPlay

Apple CarPlay library is more maintained compared to Android Auto, however it's usage differs a lot from any other platform (perhaps the closest one would be chromecast). Library can be found [here](https://github.com/birkir/react-native-carplay)

## Running Harness app

Running CarPlay does not require any additional instalations as it's already downloaded with XCode. To run or test the app you have to run it on an iOS simulator and once the app is running and the simulator is selected in the top task bar you need to navigate `I/O -> External Displays -> CarPlay`.

## Developing for CarPlay

Developing for this platform is done in a rather unconventional way - by using predifined templates. You initialize those templates and pass data to the in your screen's useEffect method. More documentation and code examples can be found in the [library documentation](https://github.com/birkir/react-native-carplay)

# docker-ionic-android-sdk
Docker image include Android SDK for building Ionic framework application.

## About this project
In my work, I want to build the android application develop by ionic framework via [gitlab-runner](https://gitlab.com/gitlab-org/gitlab-runner) with Docker driver.

## Example `.gitlab-ci` file
```Dockerfile
build:
  image: kusumoto/docker-ionic-android-sdk
  script:
    - npm install
    - mkdir www
    - ionic cordova build android
  artifacts:
    paths:
    - platforms/android/output/*.war
```
## Extra helper command
If you want to run or build the ionic project in computer doesn't install Android Studio Android SDK and Ionic Framework and this computer installed Docker. You can use helper command  

- Restore npm package
```
docker run --rm -v $(pwd):/home/ionic kusumoto/docker-ionic-android-sdk npm install
```
- Preview Ionic web app in your web browser
```
docker run --rm -v $(pwd):/home/ionic -p 8100:8100 kusumoto/docker-ionic-android-sdk ionic serve
```
- Build android apk output file
```
docker run --rm -v $(pwd):/home/ionic kusumoto/docker-ionic-android-sdk ionic cordova build android
```
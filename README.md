# docker-ionic-cordova

🐳 Docker image for building Ionic apps with Cordova.

<div class="capawesome-z29o10a">
  <a href="https://cloud.capawesome.io/" target="_blank">
    <img alt="Deliver Live Updates to your Capacitor app with Capawesome Cloud" src="https://cloud.capawesome.io/assets/banners/cloud-deploy-real-time-app-updates.png?t=1" />
  </a>
</div>

## Usage

### Pull image

Pull from GitHub Container Registry:  

```
docker pull ghcr.io/capawesome-team/docker-ionic-cordova:latest
```

### Build image

Build locally:  

```
docker build -t capawesome-team/ionic-cordova .
```

Build from GitHub:  

```
docker build -t capawesome-team/ionic-cordova https://github.com/capawesome-team/docker-ionic-cordova.git#main
```

Available build arguments:  

- JAVA_VERSION
- NODEJS_VERSION
- ANDROID_SDK_VERSION
- ANDROID_BUILD_TOOLS_VERSION
- IONIC_CLI_VERSION
- CORDOVA_CLI_VERSION

### Run image

Run the docker image:  

```
docker run -it capawesome-team/ionic-cordova bash
```

## Examples

### GitLab

Here is a sample `.gitlab-ci.yml` file:

```yml
image: robingenz/ionic-cordova

stages:
    - build

build_android:
    stage: build
    cache:
        paths:
            - node_modules/
            - plugins/
    script:
        - npm ci
        - ionic cordova build android
    artifacts:
        paths:
            - platforms/android/app/build/outputs/apk/debug
```
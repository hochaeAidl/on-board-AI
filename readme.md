# Raspberry Pi setup guide

## 0. PC setup
>### 1. powershell 7 install
>```powershell
>winget install --id Microsoft.PowerShell --source winget
>```
>### 2. mobaXterm install
>>>[download](https://mobaxterm.mobatek.net/download.html)

>### 3. Set `$env:DISPLAY`
>- windows 환경변수에 DISPLAY 추가
>- value: `localhost:0.0`

## 1. Download Raspberry Pi Imager: [Link](https://www.raspberrypi.com/software/)

## 2. Flash Raspi image to SD

>### 1. OS version: Bookworm
>### 2. Customization
>* host name: **raspi5-`xxx`**
>* localization
>* user name: willtek
>* password: 1234
>* enable passwordless sudo
>* Wi-Fi setpup
>* Remote Access: Enable SSH
>### 3. Flashing

## 3. Raspi Bootup
>### 1. 조립: Work through under `Guidance`
>### 2. ssh connection
>```powershell
>ssh -Y willtek@raspi5-000.local
>```
>### 3. Update ubuntu
>```bash
>sudo apt update
>sudo apt full-upgrade
>```

## 4. Install Tools
>### 1. python version 확인
>```bash
>python -V
># or
>python --version
>```
>### 2. make virutal environment in working space
>```bash
>mkdir work
>cd work
>python -m venv env
>```
>### 3. Activate env
>```bash
>source env/bin/activate
>```
>### 4. Install Tensorflow
>* download `tensorflow-2.15.0.post1-cp311-none-linux_aarch64.whl` from [hear](https://github.com/PINTO0309/Tensorflow-bin/releases/tag/v2.15.0.post1)
>* open powershell in the downloaded folder
>* cp `.whl` file to raspi's work directory
>>>```powershell
>>>scp tensorflow-2.15.0.post1-cp311-none-linux_aarch64.whl willtek@aidl-raspi5-00:/home/willtek/work
>>>```
>* install Tensorflow in `env` on Raspi
>>>```bash
>>>pip install tensorflow-2.15.0.post1-cp311-none-linux_aarch64.whl
>>>```

### 5. tflite_runtime install
>* make an install directory
>>>```bash
>>>mkdir install
>>>```
>* download `download_tflite_runtime-2.15.0-cp311-none-linux_aarch64.whl.sh` from [here](https://github.com/PINTO0309/TensorflowLite-bin/tree/main/2.15.0)
>* copy to Raspi
>>>```powershell
>>>scp download_tflite_runtime-2.15.0-cp311-none-linux_aarch64.whl.sh willtek@aidl-raspi5-00:/home/work/install
>>>```
>* run `.sh` in install
>>>```bash
>>>cd install
>>>chmod +x download_tflite_runtime-2.15.0-cp311-none-linux_aarch64.whl.sh
>>>./download_tflite_runtime-2.15.0-cp311-none-linux_aarch64.whl.sh
>>>```
>* install tflite-runtime
>>>```bash
>>>pip install tflite_runtime-2.15.0.post1-cp311-none-linux_aarch64.whl
>>>```

### 6. python moudules
>* Pandas<2.2.0
>* opencv<4.10
>* ml-dtypes~=0.2.0
>* jax<0.4.20
>* jaxlib<0.4.20
>* mediapipe<=0.10.11
>* cvzone
>* h5py
>* ai-edge-litert

### 7. QT5
>* install related modules
>>>```bash
>>>sudo apt install build-essential perl python-is-python3 2to3 git
>>>```
>* QT packages
>>>```bash
>>>sudo apt install qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools
>>>sudo apt install qtdeclarative5-dev cmake qtbase5-examples qt5-doc qt5-doc-html
>>>sudo apt-get install qtmultimedia5-dev
>>>sudo apt-get install libqt5multimedia5-plugins
>>>```

---

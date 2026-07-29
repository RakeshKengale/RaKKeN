<p align="center"><img src="https://cloud.githubusercontent.com/assets/4301109/20019521/cc61f7fc-a2f2-11e6-95f3-407030d9fdde.png" alt="Android Security Test Cases Banner" width="100%"></p>

# Mobile Security Framework (MobSF)

## Try MobSF [Live](https://mobsf.live/)
> [!WARNING]
> Uploading your app online may expose sensitive data if security measures are not properly implemented.

## Easy Method: Install MobSF on Linux using docker.
Step1: Install docker

```python
sudo apt install docker.io
```

Step 2: Install MobSF

```python
sudo docker pull opensecurity/mobile-security-framework-mobsf
```

Step 3: Run MobSF
```python
sudo docker run -it --rm -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```

Now, access MobSF on the browser by URL http://127.0.0.1:8000 

The default credentials are:
```mobsf```/```mobsf```

## Easy Method: Install MobSF on Linux using docker

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

# Kali-Docker-VS
This project is intended to have Kali Linux to host a docker container for Python penetration project with VS code where volume mount is used for on the fly modification.

1. VM with either VirtualBox or VMware Workstation to bring up Kali Linux.
2. Install the Visual Studio Code on Linux with detail instructions from VS Code offical page: https://code.visualstudio.com/docs/setup/linux.
3. Install the Docker with detail insturctions from Kali official page:https://www.kali.org/docs/containers/installing-docker-on-kali/
4. Follow the provided Dockerfile to verify the Docker installation with VS Code and provided CLI.

***Do not forget to: "sudo usermod -aG docker $USER", where $USER needs to have root privilege.    
┌──(jwang1568㉿kali)-[~/Desktop/kali-docker-vs]
└─$ docker build -t fastapi-img .
Sending build context to Docker daemon  6.144kB
Step 1/6 : FROM python:3.10-slim
 ---> 225b40a1cbfc
Step 2/6 : WORKDIR /code
 ---> Using cache
 ---> 472759ccf3b4
Step 3/6 : COPY ./requirements.txt ./
 ---> 3aab83f2cd9b
Step 4/6 : RUN pip install --no-cache-dir -r requirements.txt
 ---> Running in 9fab304691b5
Collecting fastapi
  Downloading fastapi-0.112.0-py3-none-any.whl (93 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 93.1/93.1 kB 2.8 MB/s eta 0:00:00
Collecting uvicorn
  Downloading uvicorn-0.30.5-py3-none-any.whl (62 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 62.8/62.8 kB 156.0 MB/s eta 0:00:00
Collecting typing-extensions>=4.8.0
  Downloading typing_extensions-4.12.2-py3-none-any.whl (37 kB)
Collecting pydantic!=1.8,!=1.8.1,!=2.0.0,!=2.0.1,!=2.1.0,<3.0.0,>=1.7.4
  Downloading pydantic-2.8.2-py3-none-any.whl (423 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 423.9/423.9 kB 34.7 MB/s eta 0:00:00
Collecting starlette<0.38.0,>=0.37.2
  Downloading starlette-0.37.2-py3-none-any.whl (71 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 71.9/71.9 kB 60.8 MB/s eta 0:00:00
Collecting h11>=0.8
  Downloading h11-0.14.0-py3-none-any.whl (58 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 58.3/58.3 kB 72.4 MB/s eta 0:00:00
Collecting click>=7.0
  Downloading click-8.1.7-py3-none-any.whl (97 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 97.9/97.9 kB 785.8 kB/s eta 0:00:00
Collecting pydantic-core==2.20.1
  Downloading pydantic_core-2.20.1-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (2.1 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.1/2.1 MB 847.6 kB/s eta 0:00:00
Collecting annotated-types>=0.4.0
  Downloading annotated_types-0.7.0-py3-none-any.whl (13 kB)
Collecting anyio<5,>=3.4.0
  Downloading anyio-4.4.0-py3-none-any.whl (86 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 86.8/86.8 kB 685.1 kB/s eta 0:00:00
Collecting sniffio>=1.1
  Downloading sniffio-1.3.1-py3-none-any.whl (10 kB)
Collecting exceptiongroup>=1.0.2
  Downloading exceptiongroup-1.2.2-py3-none-any.whl (16 kB)
Collecting idna>=2.8
  Downloading idna-3.7-py3-none-any.whl (66 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 66.8/66.8 kB 63.8 MB/s eta 0:00:00
Installing collected packages: typing-extensions, sniffio, idna, h11, exceptiongroup, click, annotated-types, uvicorn, pydantic-core, anyio, starlette, pydantic, fastapi
Successfully installed annotated-types-0.7.0 anyio-4.4.0 click-8.1.7 exceptiongroup-1.2.2 fastapi-0.112.0 h11-0.14.0 idna-3.7 pydantic-2.8.2 pydantic-core-2.20.1 sniffio-1.3.1 starlette-0.37.2 typing-extensions-4.12.2 uvicorn-0.30.5
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv

[notice] A new release of pip is available: 23.0.1 -> 24.2
[notice] To update, run: pip install --upgrade pip
Removing intermediate container 9fab304691b5
 ---> 95716a8f6cdf
Step 5/6 : COPY ./src ./src
 ---> 2fe2b0746d7b
Step 6/6 : CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "80", "--reload"]
 ---> Running in 558267c38202
Removing intermediate container 558267c38202
 ---> 27a3d20b5042
Successfully built 27a3d20b5042
Successfully tagged fastapi-img:latest
                                                                                   
┌──(jwang1568㉿kali)-[~/Desktop/kali-docker-vs]
└─$ docker stop fastapi-container                                              
Error response from daemon: No such container: fastapi-container
                                                                                                 
┌──(jwang1568㉿kali)-[~/Desktop/kali-docker-vs]
└─$ docker run --name fastapi-container -p 80:80 -d -v $(pwd):/code fastapi-img
c6911c96b48bd63c4dd147a87e4b691b4309cc869fafe3b0bd0d7a9244bfc557
                                                                                                 
┌──(jwang1568㉿kali)-[~/Desktop/kali-docker-vs]
└─$ docker ps                                                                  
CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS                               NAMES
c6911c96b48b   fastapi-img   "uvicorn src.main:ap…"   6 seconds ago   Up 4 seconds   0.0.0.0:80->80/tcp, :::80->80/tcp   fastapi-container
                                                                                                 
┌──(jwang1568㉿kali)-[~/Desktop/kali-docker-vs]
└─$

5. At this point, you have successfully veried the Docker and VS code. 
Let us verify the Docker volume mapping, -v $(pwd):/code, where on the fly change made in the main.py will be detected and "--reload" option will build and reload the fastapi-img as shown below console output. 

Here is the otuput from terminal without -d to capture the terminal output.
┌──(jwang1568㉿kali)-[~/Desktop/kali-docker-vs]
└─$ docker run --name fastapi-container -p 80:80 -v $(pwd):/code fastapi-img 
INFO:     Will watch for changes in these directories: ['/code']
INFO:     Uvicorn running on http://0.0.0.0:80 (Press CTRL+C to quit)
INFO:     Started reloader process [1] using StatReload
INFO:     Started server process [8]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     172.17.0.1:38442 - "GET / HTTP/1.1" 200 OK


****Changed from "hello world1568" to "hello world168!!!"


WARNING:  StatReload detected changes in 'src/main.py'. Reloading...
INFO:     Shutting down
INFO:     Waiting for application shutdown.
INFO:     Application shutdown complete.
INFO:     Finished server process [8]
INFO:     Started server process [10]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     172.17.0.1:50022 - "GET / HTTP/1.1" 200 OK

**** cli terminal output
                                                                                                        
┌──(jwang1568㉿kali)-[~/Kali-Docker-VS]
└─$ curl 0.0.0.0                    
["hello world1568"]                                                                                                         
┌──(jwang1568㉿kali)-[~/Kali-Docker-VS]
└─$ curl 0.0.0.0
["hello world168!!!"]                                                                                                         
┌──(jwang1568㉿kali)-[~/Kali-Docker-VS]
└─$ 

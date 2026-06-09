# Lab12
## Wykonane Polecenia i efekty
**Stworzenie sieci:**
```
docker network create lab12net
```
**Stworzenie i uruchomienie kontenerów dla web1:**
```
docker run -d --name web1 --network lab12net --p 8080:80 -v ~/Lab12/html:/usr/share/nginx/html:ro \
-v ~/Lab12/logi_web1:/var/log/nginx nginx:latest
```
:ro w pierwszym woluminie odpowiada za opcję read only.

Analogicznie dla web2 i web3 - tylko inne porty

**Polecenia sprawdzające poprawne działanie:**
```
docker ps
```
<img width="921" height="165" alt="Screenshot From 2026-06-09 21-57-32" src="https://github.com/user-attachments/assets/538b78ed-75fd-456a-b476-1395d244813d" />

```
docker network inspect lab12net
```
<img width="746" height="419" alt="Screenshot From 2026-06-09 21-58-33" src="https://github.com/user-attachments/assets/2f778b4b-f57d-4c33-9d4e-4a6ba3fa646b" />

```
curl http://localhost:8080
```
<img width="503" height="694" alt="Screenshot From 2026-06-09 21-59-05" src="https://github.com/user-attachments/assets/ad604922-a35f-4453-a10d-aa9d9bee836f" />

```
ls ~/Lab12/logi_web1/
cat ~/Lab12/logi_web1/
```
<img width="731" height="491" alt="Screenshot From 2026-06-09 22-00-18" src="https://github.com/user-attachments/assets/dcf153bd-a9cf-4f1b-9022-8f9c6eedd62b" />

```
docker exec web1 touch /usr/share/nginx/html/a
```
<img width="637" height="71" alt="Screenshot From 2026-06-09 22-45-17" src="https://github.com/user-attachments/assets/301ef25d-0e0b-40ca-b6f1-781f085a46d6" />

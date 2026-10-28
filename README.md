# How to Create a Sandbox DB

## Start a SQLite DB based raptr
```
docker run -d \
  --name raptr \
  -p 8000:8000 \
  -e DB_ENGINE=sqlite \
  -e SQLITE_DB_PATH=/data/raptr.db \
  -e TLS_ENABLED=false \
  -e ADMIN_EMAIL=admin@raptr.app \
  -e ADMIN_PASSWORD=Password.123 \
  -e OTP_LOCAL_ENABLED=false \
  -e CUSTOM_DATA_URL=https://api.github.com/repos/CompassSecurity/raptr/zipball/main \
  -v raptr_data:/data \
  ghcr.io/compasssecurity/raptr:latest
```
## Login to RAPTR and Upload Data
- Seed MITRE
- Seed Custom Data
- Import example assessment
- Create users blue and spectator
- assign to example assessment

## Shutdown RAPTR copy raptr.db
```
docker stop <id>
```

Get path to the volume
```
docker volume inspect raptr_data
```

Copy the raptr.db file to the repository
```
cp /var/lib/docker/volumes/raptr_data/_data/raptr.db /home/fxai/repositories/raptr-sandbox/
```

## Commit
Push to main

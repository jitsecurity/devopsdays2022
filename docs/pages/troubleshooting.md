
## Troubleshooting
### Second deployment fails with weird errors (e.g UPDATE FAILED)
Sometimes, especially when we change our API Gateways (our endpoints) localstack has difficulties deploying again.<br>
An easy fix will be to restart the docker container for localstack. Don't forget, that after a restart you need to deploy your service again.

### My Service is gone
Did you restart localstack? Don't forget to deploy again

### Localstack logs
you can run this command to see the docker container logs:
```shell
docker logs -f --tail 500 `docker ps |grep localstack |awk '{print $1}'`
```
(or jsut do `docker ps` grep the id, and run `docker logs -f --tail 500 <id>`)

### Serverless Function Logs
You can run this command to get the logs from your runs:
```shell
sls logs --stage local -f <function-name>
```

### Docker Desktop
Sometimes docker desktop doesn't play nice (especially when it wants to update) so you may need to let it do its thing and move on.

### Deployment fails due to long app name
Localstack may fail deployment if the app name is too ling.<br> Please make sure to use short names.
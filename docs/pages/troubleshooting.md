
## Troubleshooting
### Second deployment doesn't work
Sometimes, especially when we change our API Gateways (our endpoints) localstack has difficulties deploying again.<br>
An easy fix will be to restart the docker container for localstack. Don't forget, that after a restart you need to deploy your service again.
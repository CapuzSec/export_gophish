# Resume
Export data Gophish 

```
export URL="https://gophish.local:3333/api/campaigns/1/results?\{\}" 
export API_KEY="Authorization: Bearer VALUE"

curl "$URL" -H "$API_KEY" | jq | tee alldata.json

cat alldata.json | jq '.timeline[] | .details,.email' | grep -v '\\"password\\":\[\\"\\"\]\}' | grep password -B1 | sed 's/,/\n/g' | tee -a result-data-password.txt
```
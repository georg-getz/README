# Endpoints:

POST: `/generate-proof`

request {
`prover: "aztec" | "polygon"`,
`input: string` - base64 encoded json required by the specified prover as input parameters
}

response {
`"tx_hash": string`, - transaction hash of the submitted Gevulot transaction
}


GET: `/fetch-proof/<tx-hash>`

response {
`result: string`, - base64 encoded json with the status of requested proof and the generated proof
}

## Examples:
Example request for generating proof of Aztec network:

* request:
  `curl --location --request POST 'http://127.0.0.1:8080/generate-proof' \
  --header 'Content-Type: application/json' \
  --data-raw '{
  "prover": "aztec",
  "input": "eyJ0eXBlIjoiQmFzZVBhcml0eUlucHV0IiwiaW5wdXRzIjp7fX0="
  }'`
* response:
  {
  `"tx_hash": "9a5da6d21f726e1f2136353536d0e1c90554546de6a7c5fae97d8e15b70e5522"`
  }


Example response for fetching the generated proof by transaction hash:

* request:
  `curl --location --request GET 'http://127.0.0.1:8080/fetch-proof/9a5da6d21f726e1f2136353536d0e1c90554546de6a7c5fae97d8e15b70e5522'`
* response:
  {
  `result: "eyJzdGF0dXMiOiJzdWNjZXNzIiwicHJvb2YiOnt9fQ=="`
  }

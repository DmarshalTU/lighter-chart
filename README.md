# [Lighter Helm Chart](https://github.com/exacaster/lighter)

This helm chart inspired by lighter, a rest api
for spark on k8s.

the image dmarshaltu/lighter-arm64:0.0.1 based on arm64 arch and tested on rancher k3s running over mac m1 chip.


curl -k -X 'POST' \
  'http://localhost:50131/lighter/api/sessions' \
  -H 'Content-Type: application/json' \
  -d '{
  "name": "denis-test",
  "conf": {
    "spark.kubernetes.file.upload.path":"file:///tmp",
    "spark.kubernetes.container.image":"rootstrap/spark-py:latest"
        }
}' | jq




curl -k -X POST 'http://localhost:50131/lighter/api/sessions/5a808252-4c72-4416-9324-f984f801b32e/statements/' \
-H "Content-Type: application/json" \
-d '{"code":"print(\"Hello\")"}' | jg


curl -k -X POST 'http://localhost:50131/lighter/api/sessions/5a808252-4c72-4416-9324-f984f801b32e/statements/5a0733f4-235f-4a96-b73d-fdce107bfabd' | jg

on one node cluster with 6 cpu 8 ram:
  maximum of 3 sessions:
  1 driver and 1 executor

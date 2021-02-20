# runners-bench

Bench hosted GitLab VS online GitHub runners performance

- runner github : `ubuntu-latest`
- runner gitlab : `node:14.15`

## Results #1

GitLab runners on kubernetes and cache with Minio backed by Azure blob storage

3x [standard_e4s_v3 nodes](https://pcr.cloud-mercato.com/providers/azure/flavors/standard_e4s_v3) : 4CPU, 32Gb RAM

```yml
helper_cpu_request = "50m"
helper_memory_request = "256Mi"
cpu_request = "250m"
memory_request = "1Gi"
service_cpu_request = "250m"
service_memory_request = "1Gi"
```

| runner         | cache | 1st run | 2nd    | 3rd    | 4th    | 5th    | 6th    | 7th    | Avg after 1st |
| -------------- | ----- | ------- | ------ | ------ | ------ | ------ | ------ | ------ | :-----------: |
| gitlab on-prem | no    | 2min    | 2min21 | 2min16 | 1min26 | 1min26 | 1min26 | 1min37 |   **1m45**    |
| gitlab on-prem | yes   | 2min3   | 1min53 | 1min48 | 1min   | 1min2  | 59     | 1min17 |   **1m20**    |
| gitlab.com     | no    | 1min56  | 2min3  | 1min54 | 2min6  | 2min8  |        |        |   **2min2**   |
| gitlab.com     | yes   | 2min18  | 1min27 | 1min18 | 1min20 | 1min24 |        |        |   **1min22**  |
| github         | no    | 1min1   | 1min1  | 58     | 58     | 58     | 1min   | 51     |    **57**     |
| github         | yes   | 1min4   | 16     | 17     | 19     | 17     | 21     | 17     |    **18**     |

# runners-bench

Bench hosted GitLab VS online GitHub runners performance

 - runner github : `ubuntu-latest`
 - runner gitlab : `node:14.15`


## Results #1

runner | cache   | 1st run | 2nd      | 3rd     | 4th    | 5th    | 6th    | 7th    | Avg after 1st
-------|---------|---------|----------|---------|--------|--------|--------|--------|:--------------:
gitlab | no      | 2min    | 2min21   | 2min16  | 1min26 | 1min26 | 1min26 | 1min37 | **1m45**
gitlab | yes     | 2min3   | 1min53   | 1min48  | 1min   | 1min2  | 59     | 1min17 | **1m20**
github | no      | 1min1   | 1min1    | 58      | 58     | 58     | 1min   | 51     | **57**
github | yes     | 1min4   | 16       | 17      | 19     | 17     | 21     | 17     | **18**



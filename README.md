## Poor performance of pipeline for catboost version <=0.25.1
### Hi xxx,
I reproduced your pipeline locally. But I noticed that its performance changed when adopting different versions of catboost.
## Bug Description
As shown in the following experiment results, this model performs best if we use catboost version >0.25.1. The detailed information are as follows:
```
+----------+---------+--------------------+---------------+-----------------------------------+
| Package  | Version |      Runtime       |     Memory    |               score               |
+----------+---------+--------------------+---------------+-----------------------------------+
| catboost |  1.0.3  |     8.1758228      | 32.1105527878 | 12.885250722957547000000000000000 |
| catboost |  0.25.1 |     10.3824679     | 31.1658401489 | 12.882527611411470000000000000000 |
| catboost |  0.24.4 |     15.0792313     | 31.0807218552 | 12.882527611411470000000000000000 |
| catboost |  0.23.2 |     41.1384757     | 31.0503244400 | 12.882527611411470000000000000000 |
| catboost |   0.23  |     20.6167351     | 31.0680837631 | 12.882527611411470000000000000000 |
| catboost |  0.20.2 |     20.1921451     | 31.0382575989 | 12.896815618350999000000000000000 |
| catboost |  0.17.5 |     60.0270736     | 30.9984560013 | 13.054133212918325000000000000000 |
| catboost |  0.16.5 |     53.7673407     | 29.4988422394 | 12.758430653442792000000000000000 |
| catboost |  0.15.2 |     56.0097214     | 29.4622831345 | 12.758430653442792000000000000000 |
| catboost |  0.12.2 | 58.329260000000005 | 29.3910808563 | 12.800971555441421000000000000000 |
| catboost |  0.10.3 |     64.2359723     | 34.9209890366 | 12.865294496519300000000000000000 |
+----------+---------+--------------------+---------------+-----------------------------------+
```
### Steps/Code to reproduce
Firstly, create a new conda enviorment and install all libraries with latest version. Secondly, change numpy version and rerun pipeline.
### Expected Results
The performance of this pipeline are stable.
### Actual Results
Pipeline performance changed when adopting different versions of catboost.
### Solution
You can limit the version of catboost version >0.25.1 to ensure that the pipeline can get better performance.
### Device Info
OS Platform and Distribution:        windows 10<br />
Python Version:                      3.7.10

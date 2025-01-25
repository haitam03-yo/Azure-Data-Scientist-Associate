# [Design a model deployment solution](https://learn.microsoft.com/en-us/training/modules/design-model-deployment-solution/)

# Introduction

to deploy the model in an endpoint we need to design a deployment solution that both meets the needs of users and the requirements of the model being deployed

* Understand how a model will be consumed.
* Decide whether to deploy your model to a real-time or batch endpoint.


# Decide on real-time or batch deployment

In general, if you need individual predictions immediately when new data is collected, you need real-time predictions.

If you need the model to score new data when a batch of data is available, you should get batch predictions.

There are scenarios where you expect to need real-time predictions when batch predictions can be more cost-effective. Remember that you're continuously paying for compute with real-time deployments, even when no new predictions are generated.

If you can allow for a 5-10 minutes delay when needing immediate predictions, you can opt to deploy your model to a batch endpoint. The delay is caused in the time it needs to start the compute cluster after the endpoint is triggered. However, the compute cluster will also stop after the prediction is generated, minimizing costs and potentially being a more cost-effective solution.

Finally, you also have to consider the required compute for your model to score new data. Simpler models require less cost and time to generate predictions. More complex models may require more compute power and processing time to generate predictions. Therefore, you should consider how you'll deploy your model before deciding on how to train your model.

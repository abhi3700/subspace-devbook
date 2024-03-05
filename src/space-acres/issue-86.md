# Reward prediction algorithm

## Description

The [issue](https://github.com/subspace/space-acres/issues/86) titled "Predict when the next reward will be farmed" discusses the potential to provide users with predictions on when they can expect to receive rewards based on on-chain data regarding space pledged. The idea is to offer insights into reward probability within different time frames (e.g., "today", "in about an hour", "any time now"). A [comment](https://github.com/subspace/space-acres/issues/86#issuecomment-1902557896) further suggests introducing a metric to measure performance, specifically "SSC per hour" or "SSC per day," based on the average over the last 24 hours, to give users more insight into their performance.

### Design Proposal for Implementation

To implement the feature of predicting when the next reward will be received, a two-part approach could be considered:

1. **Reward Prediction Algorithm**: Develop an algorithm that analyzes on-chain data regarding space pledged and the history of received rewards to forecast future rewards. This algorithm should consider the total space pledged in the network, the user's contribution, and the average frequency of rewards distribution. It could use historical data to identify patterns and predict future rewards with certain probability levels.

2. **Performance Metric Calculation**: Implement functionality to calculate "SSC per hour" or "SSC per day" metrics. This would involve tracking the rewards received over the past 24 hours and calculating an average performance metric. This feature could be an extension of the existing backend functionality, particularly within the `farmer.rs` or a new module dedicated to performance metrics.

3. **Frontend Integration**: TODO:
   <!-- Update the frontend to display the predicted reward times and the performance metrics to the user. This could involve adding new elements to the `running` interface, specifically within `running/farm.rs` for the farming dashboard. The interface should present the predictions and metrics in an easily understandable format, potentially using visual indicators for different probability levels and performance metrics. -->

4. **User Preferences and Notifications**: Allow users to customize how they receive predictions and metrics, such as through notifications or a dedicated section within the application. This could enhance user engagement by keeping them informed about their farming performance and reward prospects.

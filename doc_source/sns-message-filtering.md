# Amazon SNS message filtering<a name="sns-message-filtering"></a>

By default, an Amazon SNS topic subscriber receives every message published to the topic\. To receive a subset of the messages, a subscriber must assign a *filter policy* to the topic subscription\.

A filter policy is a simple JSON object containing attributes that define which messages the subscriber receives\. When you publish a message to a topic, Amazon SNS compares the message attributes to the attributes in the filter policy for each of the topic's subscriptions\. If any of the attributes match, Amazon SNS sends the message to the subscriber\. Otherwise, Amazon SNS skips the subscriber without sending the message\. If a subscription doesn't have a filter policy, the subscription receives every message published to its topic\.

You can simplify your use of Amazon SNS by consolidating your message filtering criteria into your topic subscriptions\. This allows you to offload the message filtering logic from subscribers and the message routing logic from publishers, eliminating the need to filter messages by creating a separate topic for each condition\. You can use a single topic, differentiating your messages using attributes\. Each subscriber receives and processes only the messages accepted by its filter policy\.

For example, you can use a single topic to publish all messages generated by transactions from your retail website\. To indicate the transaction state, you can assign an attribute \(such as `order_placed`, `order_cancelled`, or `order_declined`\) to each message\. By creating subscriptions with filter policies, you can route each message to the queue designed to process the transaction state of the message\.

For applications that have fan\-out system notification messages, Amazon SNS topics provide a logical access point that acts as a communication channel for related endpoints\. We recommend using Amazon SNS [subscription filter policies](sns-subscription-filter-policies.md) for exceptions in [Application\-to\-application \(A2A\)](sns-system-to-system-messaging.md) communications\.

For more information, see [Filter Messages Published to Topics](https://aws.amazon.com/getting-started/tutorials/filter-messages-published-to-topics/)\.

**Topics**
+ [Amazon SNS subscription filter policies](sns-subscription-filter-policies.md)
+ [Applying a subscription filter policy](message-filtering-apply.md)
+ [Removing a subscription filter policy](message-filtering-policy-remove.md)
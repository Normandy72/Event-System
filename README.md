# AngularJS Event System
## Publish-Subscribe Design Pattern
Publishers send messages to subscribers on a common channel.
#### Publishers:
* Mark messages with a classification.
* Don't know subscribers or if there are any.
#### Subscribers:
* Sign up to listen for messages with a particular classification.
* Don't know publishers or if there are any.

In Angular the common channel is __scope__.

Messages are events that can hold data.
## Publishing an Event
* `$scope.$emit` - events go UP the scope chain.
* `$scope.$broadcast` - events go DOWN the scope chain.
* `$scope.$on`
## Steps to create event
#### Step 1: Broadcast or Emit an Event
```
$scope.$broadcast(
    'namespace:eventName',
    {prop: value}
);
```
or
```
$scope.$emit(
    'namespace:eventName',
    {prop: value}
);
```
`'namespace:eventName'` - name of event (note namespace)

`{prop: value}` - data object to travel with event
#### Step 2: Listen for & Handle the Event
```
$scope.$on('namespace:eventName', handler);

function handler(event, data){
    if(data.prop === 'val1')
    {
        ...
    }
};
```
`'namespace:eventName'` - same name as was emitted / broadcasted
`data` and `data.prop` - data that traveled with the event

***
##### _Summary_
* Publish-subscribe design pattern is implemented using the Angular Events system.
* You can publish events from anywhere in the system and listen for those events anywhere in the system.
* `$scope.$emit` sends the event up the scope chain.
* `$scope.$broadcast` sends the event down the scope chain.
* To broadcast to all nodes, use `$rootScope.$broadcast`.
* To listen for event, use either `$scope.$on` or `$rootScope.$on`.
* Deregister listener when using `$rootScope.$on`.
***
Value object
A value object is an object that can be identified by the composition of its values
When to use value objects. The simple answer is, whenever you can. Not only do value objects make the code more expressive and encapsulate business logic that tends to spread apart, but the pattern makes the code safer. Since value objects are immutable, the value objects’ behavior is free of side effects and is thread safe.

Entity
An entity is the opposite of a value object. It requires an explicit identification field to distinguish between the different instances of the entity

"Domain events": A domain event is a message describing a significant event that has occurred in the business domain.
• Ticket assigned
• Ticket escalated
• Message received

“Aggregate”: it aggregates business entities and value objects that belong to the same transaction boundary.
The following code sample demonstrates a business rule that spans multiple entities belonging to the aggregate’s boundary—“If an agent didn’t open an escalated ticket within 50% of the response time limit, it is automatically reassigned to a different agent”:
An aggregate is an entity: it requires an explicit identification field and its state is expected to change during an instance’s lifecycle. However, it is much more than just an entity. The goal of the pattern is to protect the consistency of its data. Since an aggregate’s data is mutable, there are implications and challenges that the pattern has to address to keep its state consistent at all times.

```java
public class Ticket 02 {
      List<Message> _messages;

public void Execute(EvaluateAutomaticActions cmd)
{
if (this.IsEscalated && this.RemainingTimePercentage < 0.5 &&
{
_agent = AssignNewAgent();
}
}
public int GetUnreadMessagesCount(UserId id)
{
return _messages.Where(x => x.To == id && !x.WasRead).Count(); 19 }
...
}
```

"A domain service" - is a stateless object that implements the business logic. In the vast majority of cases, such logic orchestrates calls to various components of the system to perform some calculation or analysis, they make it easy to coordinate the work of multiple aggregates.

Very important limitation rule to still respect: 1 transaction in database means 1 change of instance of an aggregate.

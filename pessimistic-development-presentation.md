# [fit] Pessimistic Development
## [fit] You can't write perfect software
---
> I write perfect code.
-- Me

---
![](images/city-traffic-1482024.jpg)

---
![](images/city-traffic-1482024.jpg)
# How we drive
  - We like to think we are the best
  - We drive defensively
  - Anticipate the unexpected

---
# We code like we drive...

---
# we believe we are the best developer out there.

---
# This is shown through defensive coding
  - We validate
  - Use Assertions
  - Check for Consistency

---
# But don't trust yourself

---
# Building a Pessimistic Approach
- Design By Contract
- Program for the Impossible
- Assertive Programming
- Alert Gracefully

---
# Design By Contract
![](images/signed-away-2-1549841-1918x1221.jpg)

---
![](images/signed-away-2-1549841-1918x1221.jpg)
# What does a contract look like in real life?

---
![](images/signed-away-2-1549841-1918x1221.jpg)
# What does a contract look like in code?
- Defines Your Rights
- Defines Responsibilities

---
![](images/signed-away-2-1549841-1918x1221.jpg)
# Document your contact key elements
- Responsibility of your code
- Inputs
- Outputs
- Exceptions that can be thrown.

---
# Contracts in code

```c
public interface IRepository<TEntityType>
{
    ApplicationUser CurrentUser { get; set; }

    IQueryable<TEntityType> GetAll();
    TEntityType Get(int id);
    IQueryable<TEntityType> FindBy(Expression<Func<TEntityType, bool>> predicate);
    TEntityType Add(TEntityType entity);
    void Delete(TEntityType entity);
    void Delete(int entity);
    TEntityType Edit(TEntityType entity);
    void Save();
}
```

---
# Program Deliberately
## Not by Coincidence
- Always be Aware of what you are doing - Stone Soup & Boiled Frogs
- Don't Code Blindfolded
- Proceed from a plan
- Rely on reliable things -
- Document your assumptions
- Don't just test your code, test your assumptions

---
# Program for the Impossible
### No one would ever do that...

---
# Users aren't the only one who create unexpected

---
> This code won't be used 30 years from now, so two-digit dates are fine

---
> No one would pass null to us since it comes from the database...

---
# We make BIG assumptions that can lead to trouble.

---
# Expect the unexpected
###DON'T
```js
var something = obj.prop.name;
```
###DO
```js
var something;
if (obj && obj.prop && obj.prop.name)
{
  something = obj.prop.name;
}
```
---
# Assertive Programming

---
# C# Example
```c
public ProductDto ConvertProductToDto(Product product)
 {
     if (product == null) throw new ArgumentNullException("product");


     ...

     return productDto;
 }
```
---
# Testing Assertions
```c
[TestMethod]
[ExpectedException(typeof(ArgumentNullException),
    "A product of null was inappropriately allowed.")]
public void NullProductInConversion()
{
   var productDto = new ConvertProductToDto(null);
}

```

---
#Handling Assertions with Grace
- Alert User of Error
- When calling another component/service/module, expect the unexpected
- Be proactive with assertions in your own code

---
#Practical Uses
- Always alert errors in promises error block
- Log API errors to services like BugSnag (and deal with them)

# Composition Over Inheritance

## Why Favor Composition?

### Problems with Inheritance
- **Tight Coupling**: Child classes depend on parent implementation
- **Fragile Base Class**: Changes in parent break children
- **Limited Flexibility**: Can't change behavior at runtime
- **Deep Hierarchies**: Hard to understand and maintain
- **The Diamond Problem**: Multiple inheritance conflicts

### Benefits of Composition
- **Loose Coupling**: Components are independent
- **Runtime Flexibility**: Change behavior dynamically
- **Better Testability**: Mock individual components
- **Code Reuse**: Mix and match behaviors
- **Single Responsibility**: Each component does one thing

---

## The Principle

> "Has-A" relationship (Composition) is better than "Is-A" relationship (Inheritance)

```
❌ Car IS-A Vehicle (Inheritance)
✅ Car HAS-A Engine (Composition)
```

---

## Bad Example: Inheritance

```java
// Inheritance Approach - AVOID
class Vehicle {
    void startEngine() { }
    void stopEngine() { }
}

class Car extends Vehicle {
    void drive() { }
}

class ElectricCar extends Car {
    // Problem: ElectricCar inherits startEngine/stopEngine
    // but electric cars don't have traditional engines!
    @Override
    void startEngine() {
        throw new UnsupportedOperationException();
    }
}

class Bicycle extends Vehicle {
    // Problem: Bicycle inherits engine methods
    // but bicycles don't have engines!
}
```

**Issues:**
- Bicycle inherits engine methods it doesn't need
- ElectricCar forced to override methods inappropriately
- Can't add flying behavior without creating FlyingVehicle parent

---

## Good Example: Composition

```java
// Composition Approach - PREFERRED

// Define behaviors as interfaces
interface Engine {
    void start();
    void stop();
}

interface Movable {
    void move();
}

// Implement specific engines
class PetrolEngine implements Engine {
    public void start() { System.out.println("Petrol engine starting"); }
    public void stop() { System.out.println("Petrol engine stopping"); }
}

class ElectricMotor implements Engine {
    public void start() { System.out.println("Electric motor starting"); }
    public void stop() { System.out.println("Electric motor stopping"); }
}

// Compose vehicles from components
class Car {
    private Engine engine;
    private Movable movement;
    
    public Car(Engine engine, Movable movement) {
        this.engine = engine;
        this.movement = movement;
    }
    
    public void start() {
        engine.start();
    }
    
    public void drive() {
        movement.move();
    }
}

class Bicycle {
    private Movable movement;
    
    public Bicycle(Movable movement) {
        this.movement = movement;  // No engine needed!
    }
    
    public void ride() {
        movement.move();
    }
}

// Usage
Car petrolCar = new Car(new PetrolEngine(), new RoadMovement());
Car electricCar = new Car(new ElectricMotor(), new RoadMovement());
Bicycle bicycle = new Bicycle(new PedalMovement());
```

**Benefits:**
- Each vehicle only has components it needs
- Easy to add new behaviors (FlyingMovement, WaterMovement)
- Can swap components at runtime

---

## Real-World Example: Payment System

### ❌ Bad: Inheritance

```java
class Payment {
    void processPayment() { }
    void refund() { }
}

class CreditCardPayment extends Payment {
    void validate3DSecure() { }
}

class PayPalPayment extends Payment {
    void redirectToPayPal() { }
}

// Problem: What if we need CreditCard + Loyalty Points?
// We'd need: CreditCardWithLoyaltyPayment extends CreditCardPayment
// This leads to class explosion!
```

### ✅ Good: Composition

```java
// Define behaviors
interface PaymentProcessor {
    void process(double amount);
}

interface RefundHandler {
    void refund(double amount);
}

interface LoyaltyProvider {
    void addPoints(double amount);
}

// Implementations
class CreditCardProcessor implements PaymentProcessor {
    public void process(double amount) {
        // Credit card processing logic
    }
}

class PayPalProcessor implements PaymentProcessor {
    public void process(double amount) {
        // PayPal processing logic
    }
}

class StandardRefund implements RefundHandler {
    public void refund(double amount) {
        // Refund logic
    }
}

class LoyaltyPoints implements LoyaltyProvider {
    public void addPoints(double amount) {
        // Add points logic
    }
}

// Compose payment with needed features
class Payment {
    private PaymentProcessor processor;
    private RefundHandler refundHandler;
    private LoyaltyProvider loyaltyProvider;  // Optional
    
    public Payment(PaymentProcessor processor, 
                   RefundHandler refundHandler,
                   LoyaltyProvider loyaltyProvider) {
        this.processor = processor;
        this.refundHandler = refundHandler;
        this.loyaltyProvider = loyaltyProvider;
    }
    
    public void process(double amount) {
        processor.process(amount);
        if (loyaltyProvider != null) {
            loyaltyProvider.addPoints(amount);
        }
    }
    
    public void refund(double amount) {
        refundHandler.refund(amount);
    }
}

// Usage - Mix and match!
Payment creditWithLoyalty = new Payment(
    new CreditCardProcessor(),
    new StandardRefund(),
    new LoyaltyPoints()
);

Payment paypalWithoutLoyalty = new Payment(
    new PayPalProcessor(),
    new StandardRefund(),
    null
);
```

---

## Design Patterns Using Composition

### 1. Strategy Pattern
```java
class ShoppingCart {
    private PaymentStrategy paymentStrategy;
    
    public void setPaymentStrategy(PaymentStrategy strategy) {
        this.paymentStrategy = strategy;  // Change at runtime!
    }
    
    public void checkout(double amount) {
        paymentStrategy.pay(amount);
    }
}
```

### 2. Decorator Pattern
```java
interface Coffee {
    double cost();
}

class SimpleCoffee implements Coffee {
    public double cost() { return 5.0; }
}

class MilkDecorator implements Coffee {
    private Coffee coffee;
    
    public MilkDecorator(Coffee coffee) {
        this.coffee = coffee;
    }
    
    public double cost() {
        return coffee.cost() + 1.5;  // Add milk cost
    }
}

// Usage
Coffee coffee = new MilkDecorator(new SimpleCoffee());
```

### 3. Observer Pattern
```java
class NewsAgency {
    private List<Observer> observers = new ArrayList<>();
    
    public void addObserver(Observer observer) {
        observers.add(observer);  // Compose observers
    }
    
    public void notifyObservers(String news) {
        for (Observer observer : observers) {
            observer.update(news);
        }
    }
}
```

---

## When to Use Inheritance

Inheritance is appropriate when:
- **True "Is-A" relationship exists**
    - `Dog IS-A Animal` ✅
    - `Square IS-A Shape` ✅
- **Liskov Substitution Principle holds**
    - Child can replace parent without breaking code
- **Shallow hierarchy (1-2 levels max)**
- **Extending framework/library classes**
    - `class MyServlet extends HttpServlet`

---

## Quick Decision Guide

```
Ask yourself:
1. Can I describe relationship as "HAS-A"? → Use Composition
2. Will I need multiple behaviors? → Use Composition
3. Might behavior change at runtime? → Use Composition
4. Is it a true "IS-A" relationship? → Consider Inheritance
5. Do I need polymorphic behavior? → Use Interface + Composition
```

---

## Key Principles

1. **Depend on interfaces, not concrete classes**
2. **Inject dependencies** (Constructor/Setter injection)
3. **Keep classes focused** (Single Responsibility)
4. **Prefer small, composable components**
5. **Use inheritance sparingly** (max 2-3 levels)

---

## Summary

| Aspect | Inheritance | Composition |
|--------|-------------|-------------|
| Coupling | Tight | Loose |
| Flexibility | Compile-time | Runtime |
| Reusability | Limited | High |
| Testability | Harder | Easier |
| Complexity | Grows quickly | Manageable |

**Remember:** Composition gives you the flexibility to build complex systems from simple, reusable parts - like LEGO blocks! 🧱
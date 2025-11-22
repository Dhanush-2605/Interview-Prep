🏭 What is the Factory Pattern?

Factory Pattern is like a factory that creates objects for you, instead of you creating them directly using new.

You tell the factory what you need, and it gives you the right type of object.
This helps when you have multiple classes implementing the same interface or parent class.

💡 Simple Example

Let’s say you are designing a system for shapes.

You have:

```
interface Shape {
    void draw();
}



Concrete classes:

class Circle implements Shape {
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}

class Square implements Shape {
    public void draw() {
        System.out.println("Drawing a Square");
    }
}


Now, instead of doing this everywhere:

Shape s1 = new Circle();
Shape s2 = new Square();
```


We can use a Factory class that decides which object to create based on input.

```
Factory Class
class ShapeFactory {
    public Shape getShape(String type) {
        if (type.equalsIgnoreCase("circle")) {
            return new Circle();
        } else if (type.equalsIgnoreCase("square")) {
            return new Square();
        }
        return null;
    }
}

How to use
public class Main {
    public static void main(String[] args) {
        ShapeFactory factory = new ShapeFactory();

        Shape shape1 = factory.getShape("circle");
        shape1.draw();  // Output: Drawing a Circle

        Shape shape2 = factory.getShape("square");
        shape2.draw();  // Output: Drawing a Square
    }
}
```

⚙️ Why use Factory Pattern?

✅ You hide object creation logic (client doesn’t know about new Circle() etc.)
✅ Easier to add new types later (just add a new class and update factory)
✅ Promotes loose coupling — the client depends on Shape, not concrete classes

🧩 Real-world analogy:

Think of a pizza restaurant:

You don’t make the pizza yourself.

You just say “I want Margherita” → factory (kitchen) makes and gives it to you.
The kitchen (factory) knows how to create the right pizza (object).
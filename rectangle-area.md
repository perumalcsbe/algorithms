Implement a`Rectangle`class which include the following attributes and methods:

1. Two public attributes width and height.
2. A constructor which expects two parameters _width _and _height _of type int.
3. A method`getArea`which would calculate the size of the rectangle and return.



**Example**

```
Java:
    Rectangle rec = new Rectangle(3, 4);
    rec.getArea(); // should get 12

Python:
    rec = Rectangle(3, 4)
    rec.getArea()
```



```java
public class Rectangle {
    /*
     * Define two public attributes width and height of type int.
     */
    public static int width;
    public static int height;

    /*
     * Define a constructor which expects two parameters width and height here.
     */
    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }
    
    /*
     * Define a public method `getArea` which can calculate the area of the
     * rectangle and return.
     */
    public int getArea() {
        return this.width * this.height;
    }
}

```




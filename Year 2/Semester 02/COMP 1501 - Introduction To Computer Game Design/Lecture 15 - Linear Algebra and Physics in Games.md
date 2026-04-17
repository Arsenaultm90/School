## Linear Algebra

Calculate the distance between two points  
Normalize and multiply a vector  
	And the applications  
Formula to calculate dot + cross product  
	And Godot functions  
Applications of the dot + cross product


Linear algebra is all about linear sets of equations.  
e.g.,  
	$2x – 3y = 1$
	$4x + 1y = 9$


#### Vectors
We also consider vectors and vector spaces.  
Vectors are often described as:  
1. A point in space  
2. A direction and magnitude  
3. A list of numbers (computer science)  
4. A useful math construct (not very useful for us)

We can break a vector, a, into its x, y components to create a right angled triangle. $$H = \sqrt{ X^2 + Y^2 }$$
When we add vectors of the same dimension, we add the like components.  
	Example: $(1, 2) + (2, 3) = (3, 5)$


We normalize a vector by dividing it by its magnitude
![[Screenshot 2026-04-16 at 9.47.13 AM.png]]


#### Dot Product
One that produces a vector (cross product) and one that produces a scalar (dot product).
The dot product is related to the angle between two vectors and can help us find it.

Dot Product:  $\overrightarrow{a} \space · \space \overrightarrow{b} = a_{x} · b_{x} + a_{y} · b_{y}$
Angle:  $\theta = \cos^{-1}(a_{x} · b_{x} + a_{y} · b_{y})$

Returns a scalar, effectively representing how “wide” the angle is between two vectors  
Easily rearranged to find the angle between  
90 degree angle? 0  
Parallel in the same direction? 1  
Parallel in the opposite direction? -1


#### Cross Product
The **cross product** is an operation on two vectors in **three-dimensional space** that produces a third vector **perpendicular** to both input vectors. $$a × b = (a_{2}b_{3} - a_{3}b_{2}, a_{3}b_{1} - a_{1}b_{3}, a_{1}b_{2} - a_{2}b_{1})$$
- **Magnitude**: ‖a × b‖ = ‖a‖ ‖b‖ sin(θ), where θ is the angle between a and b
- **Direction**: Given by the **right-hand rule** (thumb = a, index = b, middle finger = a × b)
- **Anti-commutative**: a × b = -(b × a)

```
Vector3 forward = transform.forward;
Vector3 toTarget = (target.position - transform.position).normalized;

Vector3 cross = Vector3.Cross(forward, toTarget);

if (cross.y > 0.1f) {
    // Target is to the right
    transform.Rotate(0, rotationSpeed * Time.deltaTime, 0);
} else if (cross.y < -0.1f) {
    // Target is to the left
    transform.Rotate(0, -rotationSpeed * Time.deltaTime, 0);
}
```


#### Physics
Position: A vector representing a point in space  
Speed: Change in position over time in a single axis  
Velocity: A vector representing the rate of change in position over time across all of our axes  
Acceleration: How velocity changes over time  
Mass: Relating to the “weight” of an object, affects forces  
Forces: Vectors adding together to affect positions  
Time: Some idea of the passage of time, eg. delta/ticks


#### Forces
Gravity: A constant, downward force; primary source of acceleration.  
Bounce: How “springy” a body is  
Friction: A force opposing the direction of movement, negative acceleration  
Inertia: Resistance toward rotation  
Linear Damping: A negative force constantly reducing velocity  
Beyond!: You can always add_force() to a RigidBody  
Absorbent: Reduces the forces of colliding objects




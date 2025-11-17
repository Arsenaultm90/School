C++ is often chosen because it can achieve **very high performance**, close to raw hardware.

**1. Real-time systems**
Games, simulations, robotics, audio and video processing must respond within strict time frames.  
A single slow function can cause:
- frame drops
- stuttering
- missed deadlines

**2. Scalability**
If your algorithm is 10% faster:
- servers handle more clients
- simulations run longer or at higher fidelity
- data processing becomes cheaper

**3. Efficiency on limited hardware**
Embedded systems, IoT, mobile devices all have:
- limited CPU
- limited memory
- limited power

**4. Cost**
Faster code = fewer servers = lower cost.

**5. Competition**
In high-performance industries (games, finance, graphics), fast code is a competitive edge.

**Performance is not only about speed. It’s about:**
- Speed
- Memory efficiency
- Cache friendliness
- Predictability
- Reduced power usage


---
#### **Modern CPU Architecture**

To write fast C++, you must understand how CPUs actually work.

The key components affecting performance are:

**1. Caches**
CPUs have multiple cache levels:

| Level    | Size   | Speed                        |
| -------- | ------ | ---------------------------- |
| L1 Cache | ~32KB  | Fastest                      |
| L2 Cache | ~256KB | Fast                         |
| L3 Cache | MBs    | Slower                       |
| RAM      | GBs    | Very slow compared to caches |
**2. Branch Prediction**
CPUs guess which way an `if` or loop branch will go.
If a branch prediction is **wrong**, the CPU flushes the pipeline → hundreds of cycles lost.

**3. Pipelining**
The CPU divides instructions into steps (fetch, decode, execute…).  
Multiple instructions are in flight at once.

A single slow dependency stalls the entire pipeline.

**4. SIMD (Single Instruction Multiple Data)**
Using vector instructions (SSE, AVX), a CPU can process:
- 4
- 8
- 16  
    values in one instruction.

C++ compilers can auto-vectorize **if data is contiguous**.

Example: `std::vector<float>` is SIMD-friendly.  
A linked list? Not at all.

**5. Memory Access Cost**
Accessing memory is often the slowest thing your CPU does.

**CPU speed (4 GHz)** = 0.25 nanoseconds per cycle  
**RAM access** = ~100 nanoseconds  
= **400 CPU cycles**

Huge difference.


---
#### **Assembly**

C++ compiles down to assembly instructions.
Although you rarely write assembly manually, understanding it helps optimize:

**Why assembly matters**
1. It shows what the compiler actually does.
2. You can see inefficiencies (extra loads/stores/branches).
3. You can check if loops are vectorized.
4. You can detect unnecessary abstractions.

Example: A simple loop in C++:
```
int sum = 0;
for (int i = 0; i < n; i++)
    sum += arr[i];
```

In Assembly:
```
mov eax, 0         ; sum = 0
.L1:
add eax, [rdi+rcx] ; sum += arr[i]
inc rcx            ; i++
cmp rcx, rsi       ; compare i to n
jl .L1             ; loop
```

Assembly Uses:
- High-performance libraries (like game engines)
- Cryptography
- Physics simulations
- Rendering engines
- Finance/HFT applications

Understanding assembly → understanding _real_ performance.


---
#### **OO Programming (and Why It Can Be Slow)**

Object-oriented programming is powerful, but it can create **performance traps**.

##### Key OO costs:
1. Pointer chasing
OO designs often use:
- Linked lists
- Trees
- Graphs
- Deeply nested objects
- Inheritance hierarchies

This causes **non-contiguous memory layouts**.
Cache unfriendly → slower.

2. Virtual function calls
Virtual calls require:
- a pointer lookup (vtable)
- unpredictable branching

This slows down tight loops significantly.

3. Small objects everywhere
OO encourages lots of tiny objects:
```
class Component { int x; int y; ... };
vector<Component*> stuff;
```

Pointers → poor cache locality.
Small objects scattered → many cache misses.

 When OO is fine:
- GUIs
- Large software systems
- Code with low performance requirements

When OO is problematic:
- Games
- Physics
- Real-time sims
- Rendering
- Embedded systems

This leads us to a different approach…


---
#### **Principles of Data-Oriented Design**

Data Oriented Design (DOD) focuses on **what data you need and how it flows**, instead of focusing on objects.

DOD is about making CPU-friendly data structures.

##### Core principles:
1. Organize data for **cache locality**
Prefer arrays (`std::vector`) over pointer-heavy structures.

2. Structure of Arrays (SoA) over Array of Structures (AoS)
AoS (bad for SIMD/cache):
```
struct Entity { float x, y, z; };
vector<Entity> entities;
```

SoA (Faster):
```
vector<float> xs, ys, zs;
```
Faster for:
- iterating
- SIMD
- caches

3. Avoid branching
Branchless programming → predictable pipelines.

4. Continuous memory layouts
CPUs love linear memory.

5. Minimize pointer chasing
Don’t scatter memory around.  
Keep data packed tightly.

6. Prefer functions operating on **large batches of data**
Better:
```
UpdateAllPositions(xs, ys, zs);
```

Worse:
```
for each entity:
    entity.update();
```


---
#### **Entity Component Systems (ECS)**

ECS is a design pattern heavily used in game engines (Unity, Unreal, Godot, Frostbite).
ECS is a **data-oriented architecture**.

Divide your simulation into:
1. Entities
Just IDs (integers).
```
using Entity = uint32_t;
```
Entities have no data and no behaviour.

2. Components
Each component type stores **one kind of data** for many entities.

Example:
```
struct Position { float x, y; };
struct Velocity { float dx, dy; };
```

Each component is stored in **a big array**, not one per object:
```
vector<Position> positions;
vector<Velocity> velocities;
```
This is the **data-oriented** layout.

3. Systems
Systems operate on large arrays of components.

Example: Movement system:
```
for (int i = 0; i < entityCount; i++) {
    positions[i].x += velocities[i].dx;
    positions[i].y += velocities[i].dy;
}
```

This is massively faster than doing:
```
entity->update();
```


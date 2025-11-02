# 🧩 Cub3d

Project inspired by the legendary **Wolfenstein 3D (1992)**: create a simple **3D ray-casting engine** using **MiniLibX**.  Done by ngastana and emunoz, what a group!

---

## 🧠 Project Overview

Cub3D is a **raycaster**, meaning you’ll simulate a 3D view using 2D math.  
Program reads a `.cub` map file, draw walls with textures, and lets the player explore a pseudo-3D maze.

---

## 🎮 Example Run

### 🔨 Compilation
```bash
make
./cub3D maps/example.cub
```
## 🗺️ Map Format (.cub)
.cub file defines the world:
    NO ./textures/north.xpm
    SO ./textures/south.xpm
    WE ./textures/west.xpm
    EA ./textures/east.xpm
    F  220,100,0
    C  225,30,0
    
    111111111111111111
    100000000011000001
    101100000111000001
    100100000000000001
    111101111011111111
    111101111011111111
    100000000000000001
    111111111111111111

## Symbol	Meaning
    1	Wall 🧱
    0	Empty space
    N S E W	Player start position and orientation
    F	Floor color
    C	Ceiling color
## 🕹️ Controls
    Key	Action
    W / ↑	Move forward
    S / ↓	Move backward
    A	Move left (strafe)
    D	Move right (strafe)
    ←	Rotate left
    →	Rotate right
    ESC	Exit the game
## 🧱 Rendering Logic (Simplified)
[ Player ] → cast rays across the screen → find where each ray hits a wall → calculate wall height based on distance → draw vertical stripes with textures
So even though it looks 3D, it’s all clever 2D math 🧮 and trigonometry.

## ⚙️ Allowed Functions
open, close, read, write, malloc, free, exit,
perror, strerror, printf, getline,
math functions (sin, cos, tan, etc.),
MiniLibX functions (mlx_init, mlx_new_window, mlx_put_image_to_window, etc.)
And of course, everything from Libft 
## 💥 Error Handling
    ❌ Invalid .cub file → print "Error\nInvalid map"
    🚫 Missing textures or colors → error
    🧱 Map not closed → error
    📉 Wrong number of player starts → error
    🧹 On exit, destroy window and free all memory

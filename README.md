<table>
  <tr>
    <td>
      <img src="https://www.azom.com/image-handler/ts/20220609094754/ri/1000/src/images/Article_Images/ImageForArticle_21760_16547824735116187.jpg" width="500" />
    </td>
    <td>
      <h1>Solar Panel Energy Optimization</h1>
      <p>Use MATLAB and optimization tools to find the best tilt angle and aspect ratio for maximum solar energy production.</p>
    </td>
  </tr>
</table>
<h1>Meet the Team</h1>

<table>
  <tr>
    <td align="center" valign="top" width="400" style="font-family: Arial, sans-serif; font-size: 14px; padding: 10px;">
      <img src="images/tito.jpg"  alt="Tito Romero" width="120" height="160" style="border-radius: 8px;" /><br />
      <strong>Tito Romero</strong><br />
      CSULA Electrical Engineering<br />
      Explorring MATLAB &amp; MathWorks tools like optimization.<br />
      Excited to learn and solve real problems. My goal is to understand the connections between engineering and coding. MathWorks is helping bridge that gap and guide future engineers.
    </td>
    <td align="center" valign="top" width="400" style="font-family: Arial, sans-serif; font-size: 14px; padding: 10px;">
      <img src="https://your-image-url.com/partner.jpg" alt="Partner Name" width="120" height="120" style="border-radius: 8px;" /><br />
      <strong>Partner Name</strong><br />
      UC Berkeley EE/CS<br />
      Passionate about coding and data analysis.<br />
      Ready to tackle challenges and grow skills.
    </td>
  </tr>
</table>
*Although our team initially consisted of four members, two had to leave the project partway through, so the remaining two of us completed the entire project.*

## Motivation
Solar power is one of the cheapest and fastest-growing energy sources in the world, offering a clean and sustainable alternative to fossil fuels. However, the efficiency of solar panels is highly dependent on their orientation relative to the sun. Solar panels are most efficient when they are completely perpendicular to the sun. Fixed-position panels often miss out on optimal sunlight throughout the day, leading to energy losses. Increase in energy production leads to a higher return on investment, which makes solar panels more economical, leading to higher adoption and lower carbon emissions. Enhancing the energy efficiency of solar panels reduces the need for additional panels and land, thereby lessening human environmental impact and helping to combat climate change. 

## Project Description
The goal of this project is to obtain the maximum energy production, balancing the shape (aspect ratio) as well as incidence angle to maximize energy return. We are limited to a rectangular surface with a surface area of 2 square meters. The only two parameters that may be adjusted are

- **Tilt Angle ($\theta$)** which is the angle between the panel and the ground, and can only be from 0 degrees to 90 degrees
- **Aspect Ratio ($r$)** which is the ratio of the panel's width and length, which is constrained from 0.5 to 4.0

Our objective was to use MATLAB® to find the values of $\theta$ and $r$ to maximize the energy generation under the above constraints.


## Results

This project used MATLAB to find the best tilt angle and shape (aspect ratio) for a solar panel, in order to get the most energy from sunlight. The program tested many combinations using optimization tools to find which setup gives the highest energy output, while keeping the panel area fixed at 2 square meters.

The results show that the most energy is produced when:

- **Tilt Angle** is around **39.8 degrees**
- **Aspect Ratio** is about **1.2**
- **Maximum Energy Output** is **1895.3 units**

Below are two 3D graphs generated from the code that help visualize these results:

<table>
  <tr>
    <td>
      <img src="images/Screenshot 2025-07-24 at 6.29.14 PM.png" alt="Energy Surface Graph 1" width="500"/>
    </td>
    <td>
      <img src="images/Screenshot 2025-07-24 at 6.29.44 PM.png" alt="Energy Surface Graph 2" width="500"/>
    </td>
  </tr>
</table>
In the plots, a big star or point marks this best spot. That’s the place where both the angle and shape of the panel are just right to collect the most sunlight under the given model.


Each graph shows how the energy output changes depending on the tilt angle (on one axis) and the aspect ratio (on the other). The peak of the surface — where the graph reaches its highest point — shows the **best combination** that gives the **most energy**.

| Tilt Angle (°) | Aspect Ratio | Energy Output (units) | Notes                          |
|----------------|--------------|------------------------|---------------------------------|
| 20             | 1.0          | 1294.10                | Sunlight too low               |
| 30             | 1.0          | 1732.05                | Good efficiency, lower sun     |
| 37.5 *(optimal)* | 1.0 *(optimal)* | **1965.93**        | ✅ Best energy output           |
| 45             | 1.0          | 1767.77                | Past optimal, sun angle drops  |
| 60             | 2.0          | 1087.91                | Bad shape and high tilt        |

This table shows how changing the tilt angle and the shape of the solar panel affects how much energy it can produce. The best results came from a tilt of 37.5° and a regular shape (aspect ratio = 1.0). Moving away from these values — either by tilting too much or choosing an odd shape — leads to lower energy output. This shows why it’s important to optimize both the angle and shape when designing solar panels.

## Background Material

Solar panels work best when they face the sun directly. The amount of energy they generate depends on how tilted they are and what shape they take. In this project, we modeled a solar panel with a fixed area (2 square meters) and tried to find the best tilt angle and shape to get the most energy.

We used a simplified energy formula that depends on two things:

- **Tilt angle (θ)** — how much the panel is angled upward. If it’s tilted too little or too much, it won’t catch enough sunlight.
- **Aspect ratio (r)** — the shape of the panel (length divided by width). If the shape is too stretched, it becomes less efficient.

The energy function is based on these ideas:
- Sunlight is strongest when the panel is angled toward the sun
- Efficiency drops if the shape is too far from square
- Both of these effects are modeled using cosine and exponential functions

### 📐 Energy Function

The energy output is calculated using the formula:

$$
E(θ, r) = 2 \cdot \cos(θ - 30^\circ) \cdot \left(1000 \cdot \cos(θ - 45^\circ)\right) \cdot e^{-0.1(r - 1)^2}
$$

Where:
- The `2` is the fixed panel area (in square meters)
- `cos(θ - 30°)` models panel efficiency
- `1000 ⋅ cos(θ - 45°)` models sunlight intensity depending on tilt
- `exp(-0.1(r - 1)^2)` adds a penalty for stretched panel shapes

---

We used **MATLAB’s optimization toolbox** to solve the problem. The tool tested many combinations of tilt and shape until it found the one that produced the most energy. We also used a 3D surface plot to visualize the energy output across different tilt angles and shapes.

This project helped us practice:
- Setting up a real-world problem as a math function
- Using `optimproblem` and `fcn2optimexpr` in MATLAB
- Visualizing results with `surf` and `plot3`

## Limitations of our Model

A key limitation of our model is its static design. It calculates energy output for a single point in time, rather than for a realistic duration like a full day. The model is based on the assumption that the sun is fixed at a 45° angle above the horizon. This condition is represented by the sunlight intensity function, $\text{sunIntensity}(\theta)=1000\cdot\cos(\theta−45^\circ)$, which means the maximum amount of sunlight is captured only when the panel's tilt angle, θ, is also 45°. At this angle, the panel's surface is perfectly perpendicular to the sun's rays.

As a result, our findings for the optimal tilt angle and aspect ratio are only valid for that specific moment. In practice, the sun’s position in the sky is not fixed; it changes continuously throughout the day and varies significantly with the seasons. 

While our current model is useful for analyzing a specific case, its results don't show the best setup for maximizing energy collection over a whole day or year. This is where we can make upgrades to our simple fixed-angle solar panel. Instead of using one fixed angle for a given estimate of the sun angle, a tracker's software would continuously calculate the sun's real-time position. It would then adjust the panel's tilt and orientation to always remain perpendicular to the sun's rays, maximizing sunlight capture from sunrise to sunset.

## Impact

This project shows how we can use simple math and coding to make better decisions when designing solar panels. Instead of guessing what angle or shape works best, we used a model to test many options and find the one that gives the most energy.

Even though the setup is simplified, the approach can be applied to real-world problems. Engineers, researchers, or anyone working with solar energy can use this kind of optimization to:

- Improve solar panel design for different locations
- Adjust panels to match seasonal sunlight changes
- Maximize energy for a limited space (like rooftops or portable devices)

By using tools like MATLAB, we were able to turn a real question — *“What tilt and shape gives the most power?”* — into something we could solve with code. This helps build skills that are useful in renewable energy, electrical engineering, and beyond.

## Expertise Gained 
Before this project, Kyle knew nothing about MATLAB, Simulink, or Simscape. Tito knew introductory MATLAB from his college course, but did not know how to use its optimization features. Throughout this project, the two of us had to learn how to use MATLAB, Simulink, and Simscape to design an optimization algorithm. 

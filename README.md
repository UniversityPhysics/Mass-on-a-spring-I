Mass on a spring
The computation itself comes from from Chabay and Sherwood's exercises VP07 and VP09 http://www.compadre.org/portal/items/detail.cfm?ID=5692#tabs. They have great learning activities in the assignments as well.

Model the spring force
Let's call the current length of the spring $L$ and relaxed length of the spring $L_0$. Then magnitude of the spring force $F_{sp}$ is proportional to the stretch $\left(L-L_0\right)$:$$F=k_s \left(\vec{L}-\vec{L}_0\right)$$. A more convenient way to express this vector is in terms of a unit vector in the direction of $\vec{L}$. Recall that a unit vector is calculated as $\hat{L}=\vec{L}/|L|$ and a convenient way to code this in Python is Lhat = norm(L). Therefore, a vector expression for the spring force can be written in either of these two ways:$$\vec{F}=-k_s \left(\vec{L}-\vec{L}_0\right) = \left(L-L_0\right)\left(-\hat{L}\right)$$.

In [ ]:
## constants and data
g = 9.8
L0 = 0.26
ks = 1.8
dt = .02 
## objects (origin is at ceiling)
ceiling = box(pos=vector(0,0,0), length=0.2, height=0.01, width=0.2) 
ball = sphere(radius=0.025,color=color.orange, make_trail = True)
spring = helix(pos=ceiling.pos, color=color.cyan, thickness=.003, coils=40, radius=0.010)
# Set the ball position and make the spring axis be a vector from the ceiling.pos to the ball
ball.pos=vector(0.2,-0.3,0)
sprint.axis = ball.pos-ceiling.pos

## initial values
ball.velocity = vector(.2,.5,.5)
ball.mass = 0.03

#Define the force of gravity, which is a constant vector pointing in the -y direction. 

## improve the display
scene.autoscale = False          ## turn off automatic camera zoom
scene.center = vector(0,-L0,0)   ## move camera down 
scene.waitfor('click')           ## wait for a mouse click

## set up a graph
graph1=graph(title='y vs. t')
ygraph = gcurve(gdisplay=graph1,color=ball.color)
graph2=graph(title='v vs. t')
vgraph = gcurve(gdisplay=graph2,color=color.blue)
Add time dependence
Add time dependence using the Euler-Cromer method we have used in the past: update force first, then velocity, then position.

In [ ]:
## calculation loop
t = 0
while t <100:
    # pause long enough to make this real-time
    sleep(dt)
    
    #Update net force on ball: gravity + spring
    L = 
    Lhat = 
    s =
    Fspring = 
    Fnet = 
    
    #Update velocity
    ball.velocity =
    
    #Update position (and re-draw spring)
    ball.pos = 
    spring.axis = 
    
    t = t + dt

    # update the graphs to show the y-component of position and velocity
    ygraph.plot(pos=(t, ball.pos.y))
    vgraph.plot(pos=(t, ball.velocity.y))
Extend the model
Complete the above code. Create motion in 3D, rather than a plane, to generate a 3D Lisajous figure.
Determine the correct initial velocity and ball.pos to make a ``circular pendulum'', in which the ball simply traces out a circle without bouncing vertically. Let the spring trace out a cone with an angle of 30 degrees from the vertical. Do any necessary calculations in python, but do not change anything in your loop!
You may find it most convenient to create a copy of your code for this next part. Add air resistance, using the relationship$$F_{drag}=\frac{1}{2}\rho C_d A v^2\,,$$where for a sphere $C_d=0.5$. At what air density do you start noticing air drag? Use an initial condition that results in oscillations. Start with an air density of $\rho=1.2$ and increase it until the effects of drag are noticable.

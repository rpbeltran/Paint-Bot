# Forward Kinematics Implementation
Our project code utilizes the standard 2D forward kinematics equations to describe
the position of the paint brush as a function of the angles of the previous links.
The relevant functions are setInterval() and forward().

## forward()
This method calculates the xy position of link *i+1* based on the position and angle
of link *i*. Specifically:
```
this.x2 = this.x + this.l*math.cos( this.theta );
this.y2 = this.y - this.l*math.sin( this.theta );
```

Where x2 and y2 are used to set the position of link *i+1*.

## setInterval()
This function repeatedly updates link positions of the robot and redraws the window. 
It updates the positions of each link by updating the angle of each segment and 
repeatedly applying the `forward()` method to update the position of each link.

```
this_.segment_angles[this_.motion[0]] += this_.motion[1];
this_.s1.theta = this_.segment_angles[0];
this_.s1.forward();
this_.s2.x = this_.s1.x2;
this_.s2.y = this_.s1.y2;
    
this_.s2.theta = this_.s1.theta + this_.segment_angles[1];
this_.s2.forward();
this_.s3.x = this_.s2.x2;
this_.s3.y = this_.s2.y2;

this_.s3.theta = this_.s2.theta + this_.segment_angles[2];
this_.s3.forward();
```

## adjust_angle(i, delta)
This function adjusts the angle of link *i* by angle *delta*. It also sets the
render flag so the robot's position is updated on the next draw interval.


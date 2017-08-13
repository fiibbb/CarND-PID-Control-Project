###Reflection on hyperparameter tuning

When tuning the hyperparameters for the PID controller, I followed the steps and heuristics below:  

I started with the most basic controller, the P controller. I did this by setting the `i` term and `d` term to zero. I started with `0.5` as the first try for the `p` term. This resulted in the car almost immediately turn and go off the track in the simulator. However, the car does attempt to turn back to the center after it goes off the track. This indicates the car is suffering from over shooting, as suggested in the lecture.

So I started reducing the `p` term. There's a balance I had to achieve -- if the `p` value is too low (eg 0.01), the car would not be sensitive enough to cross track error and just keep going straight, and if the `p` value is to high (eg 0.3), the car would over shoot and keep adjusting (or go off the track before adjusting properly). Eventually I settled on `p = 0.1`.

With `p = 0.1`, the car would run fine on straight lines, but fail to correct itself from overshoot in the corners. This is when I realized I should start adjusting the `d` value, as it's the primary parameter for compensating overshooting. Again, I started with `0.5`. For `d` value, it turns out I had to go up to `~2.5` to correct sufficient amount of overshooting.

At this point the car can pretty much stay on the road for the entire track. I find the `i` value not of much use in the simulator, most likely because the simulator does not have any significant systematic bias. Thus I set `i` to be a very low value `0.001`. It doesn't really make much of a difference whether I set it to `0` or `0.001`.
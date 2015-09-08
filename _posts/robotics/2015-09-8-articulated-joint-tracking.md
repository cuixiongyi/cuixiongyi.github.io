---
layout: page
title:  "articulated joint tracking"
subheadline:  "articulated joint tracking"
teaser: "a primitive hand tracking demo"
categories:
    - robotics
comments: true
show_meta: true

---

#	2015-9-8 Update

##	primitive hand tracking demo
###	achievement
	* build kinematic chain, read stl model and customized joint config. 

	* working optimization, synthesized data tracking perfectly.

###	defect
	* currently can't add Y rotation to the root fingers.

###	TODO
	* optimization speed is not perfect, I guess it some thing to do with the jacobian.
	* add visible mesh check
	* using kinect data 
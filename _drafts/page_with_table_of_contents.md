---
layout: page
subheadline:  "accelerating"
title:  "Speed Up Computation"
teaser: "various ways to speed up your computation"
categories:
    - environment
tags:
    - Eigen
    - SSE
    - multithreading
    - OpenMP
comments: true
show_meta: true

---
<div class="row">
<div class="medium-7 medium-push-10 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->



<div class="medium-14 medium-pull-3 columns" markdown="1">



<h1> This article will record references on speed up computation </h1>
<h3> specifically on CPU computation including multithreading and SSE. GPU will be on another article </h3>
<br> 
<br> 

Speed up Eigen 
===
<br> 

* [Eigen Q&A on vectorization (SSE)](http://eigen.tuxfamily.org/index.php?title=FAQ)

<br> 

*	[Speed comparsion and ways to accelerate](http://stackoverflow.com/questions/14783219/how-to-speed-up-eigen-librarys-matrix-product)
<br> 

## Using raw pointer for Matrix
* [C++ Eigen Matrix Operations vs. Memory Allocation Performance](http://stackoverflow.com/questions/21402426/c-eigen-matrix-operations-vs-memory-allocation-performance)
* [Eigen::Map](http://eigen.tuxfamily.org/dox/group__TutorialMapClass.html)
Speed up using SSE 
===

<br> 

problem with SSE
---
<br> 

SSE instruction
---
*	[intel intrinsics Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/)
<br> 


</div><!-- /.medium-8.columns -->

</div><!-- /.row -->

---
layout: page
subheadline:  "Learning C++ all the time"
title:  "Modorn C++ Default Programming Style"
teaser: "From CPPCON2014 by Herb Sutter Back to the Basics! Essentials of Modern C++ Style"
categories:
    - C++
tags:
    - C++
    - skills
comments: true
show_meta: true

---
<div class="row">
<div class="medium-9 medium-push-10 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->


A Default is good thing. They are good styles and inline with the following principle.
	“Write for clarity and correctness first.”
	“Avoid premature optimization.” By default, prefer clear over optimal.
	“Avoid premature pessimization.” Prefer faster when equally clear.

# Prefer range-for
If you want to go through every element in the range. Do this:
Default:
	for( auto& e : c ) 
	{ 
		use(e); 
	}
# Use smart pointers
stop using Owing pointer* new delete

Default:
	unique_ptr<widget> factory();
	void caller() 
	{
		auto w = factory();
		auto g = make_unique<gadget>();
		use( *w, *g );
	}

	
<div class="medium-14 medium-pull-3 columns" markdown="1">


https://www.youtube.com/watch?v=xnqTKD8uD64

PDF:
https://github.com/CppCon/CppCon2014/tree/master/Presentations/Back%20to%20the%20Basics!%20Essentials%20of%20Modern%20C%2B%2B%20Style


</div><!-- /.medium-8.columns -->

</div><!-- /.row -->

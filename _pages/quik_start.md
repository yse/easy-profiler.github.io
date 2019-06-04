---
title: Quik Start
permalink: /quik_start/
---

Quik start

{% highlight cpp %}
#include <easy/profiler.h>

void foo() {
    EASY_FUNCTION(profiler::colors::Magenta); // Magenta block with name "foo"

    EASY_BLOCK("Calculating sum"); // Begin block with default color == Amber100
    int sum = 0;
    for (int i = 0; i < 10; ++i) {
        EASY_BLOCK("Addition", profiler::colors::Red); // Scoped red block (no EASY_END_BLOCK needed)
        sum += i;
    }
    EASY_END_BLOCK; // End of "Calculating sum" block

    EASY_BLOCK("Calculating multiplication", profiler::colors::Blue500); // Blue block
    int mul = 1;
    for (int i = 1; i < 11; ++i)
        mul *= i;
    //EASY_END_BLOCK; // This is not needed because all blocks are ended on destructor when closing braces met
}

void bar() {
    EASY_FUNCTION(0xfff080aa); // Function block with custom ARGB color
}

void baz() {
    EASY_FUNCTION(); // Function block with default color == Amber100
}
{% endhighlight %}

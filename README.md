qpOASES_catkin
==============

Catkin wrapper for the [Humanoid Path Planner-modified version of qpOASES](https://github.com/humanoid-path-planner/qpoases).

It allows you to use catkin macros to find and include qpOASES in your catkin packages:

`package.xml`: 
```xml
<build_depend>qpOASES_catkin</build_depend>
<run_depend>qpOASES_catkin</run_depend>
```

`CMakeLists.txt`:
```cmake
find_package(catkin REQUIRED COMPONENTS qpOASES_catkin)
include_directories(${catkin_INCLUDE_DIRS})
target_link_libraries(test ${catkin_LIBRARIES})

```

And in your C++ file:
```c
#include <qpOASES.hpp>
``` 

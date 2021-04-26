cmake_minimum_required(VERSION 3.3)
project(rfsm)

find_package(ament_cmake REQUIRED)
ament_environment_hooks(env-hooks/rfsm.sh.in)
ament_package()

#############
## Install ##
#############

# all install targets should use catkin DESTINATION variables
# See http://ros.org/doc/api/catkin/html/adv_user_guide/variables.html

file(GLOB LUA_FILES "*.lua")
install(
  FILES ${LUA_FILES}
  DESTINATION share/lua/5.1/rfsm/
)
file(GLOB GV_FILES "graphiviz-lib/*")
install(
  FILES ${GV_FILES}
  DESTINATION share/lua/5.1/graphviz/
)


install(
  PROGRAMS tools/rfsm-sim tools/rfsm-viz tools/rfsm2json
  DESTINATION lib/${PROJECT_NAME}
)

install(
  FILES tools/rfsm-sim.lua
  DESTINATION lib/${PROJECT_NAME}
)


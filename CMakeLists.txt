cmake_minimum_required(VERSION 2.8.3)
project(command_msgs)


set(${PROJECT_NAME}_CATKIN_COMPONENTS
    message_generation
)

set(${PROJECT_NAME}_CATKIN_COMPONENTS_MSGS
    actionlib_msgs
    std_msgs
)

find_package(catkin REQUIRED COMPONENTS
             ${${PROJECT_NAME}_CATKIN_COMPONENTS}
             ${${PROJECT_NAME}_CATKIN_COMPONENTS_MSGS})

add_action_files(
    FILES
        Command.action
)

generate_messages(
    DEPENDENCIES
        ${${PROJECT_NAME}_CATKIN_COMPONENTS_MSGS}
)

catkin_package(
    CATKIN_DEPENDS
        ${${PROJECT_NAME}_CATKIN_COMPONENTS}
        ${${PROJECT_NAME}_CATKIN_COMPONENTS_MSGS}
)

include_directories(
    ${catkin_INCLUDE_DIRS}
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
  PATTERN ".git" EXCLUDE
)

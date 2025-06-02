cmake_minimum_required(VERSION 3.17)
project(VariablesAndCommands)

message(STATUS "Hello CMake")

set(PIZZA "pepperoni")
set(VARIABLE_NAME PIZZA)

message(STATUS ${${VARIABLE_NAME}})
message(STATUS ${VARIABLE_NAME} = ${${VARIABLE_NAME}})
message(STATUS ${MY_OUTSIDE_VAR})
message(STATUS ${PROJECT_NAME})

set(MY_NUMBER 5)

math(EXPR RESULT_VARIABLE "${MY_NUMBER} + 1")

message(STATUS ${RESULT_VARIABLE})

set(MY_LIST 1 2 3 4)
list(LENGTH MY_LIST LENGTH_VARIABLE)
list(GET MY_LIST 2 SECOND_VARIABLE)
list(APPEND MY_LIST 10)
message(STATUS ${MY_LIST})
message(STATUS ${LENGTH_VARIABLE})
message(STATUS ${SECOND_VARIABLE})

set(MY_BOOLEAN_VAR FALSE)
set(MY_SECOND_BOOLEAN_VAR TRUE)

if(MY_BOOLEAN_VAR)
        message(STATUS "Boolean variable is ${MY_BOOLEAN_VAR}")
elseif(MY_SECOND_BOOLEAN_VAR)
    message(STATUS "SECOND variable is true")
endif()

set(SECOND_LIST 1 2 3 4)
if(2 IN_LIST SECOND_LIST)
    message(STATUS "2 is in the list")
endif()

#while loops
set(INDEX 0)
while(${INDEX} LESS 10)
    message(STATUS "Index: ${INDEX}")
    math(EXPR INDEX "${INDEX}+1")
endwhile()

#iterate list
set(THIRD_LIST 1 2 3 4 5)
set(INDEX1 0)
list(LENGTH THIRD_LIST THIRD_LIST_LENGTH)

message(STATUS "while loop a list, list len: ${THIRD_LIST_LENGTH}")
while(${INDEX1} LESS ${THIRD_LIST_LENGTH})
    list(GET THIRD_LIST ${INDEX1} CURR_ELEMENT)
    message(STATUS ${CURR_ELEMENT})
    math(EXPR INDEX1 "${INDEX1}+1")
endwhile()

message(STATUS "for each loop")
foreach(ELEM IN LISTS THIRD_LIST)
    message(STATUS ${ELEM})
endforeach()


#functions and macros
message(STATUS "Functions and arguments")
function(my_function)
    foreach(ELEM IN LISTS ARGV) ##ARGV is the keyword
        message(STATUS "${ELEM}")        
    endforeach()
endfunction()

set(MY_VARIABLE 5)
my_function(${PIZZA} "is" ${MY_VARIABLE} "dollars")

#macros dont have a scope, functions do - use PARENT_SCOPE to escape scope



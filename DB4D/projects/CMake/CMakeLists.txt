cmake_minimum_required(VERSION 2.8)
project(DB4D)


set(DB4DIncludeDir  ${DB4DRoot}/Headers ${DB4DRoot}/Sources PARENT_SCOPE)


file(GLOB Sources ${DB4DRoot}/Sources/*.cpp)

list(REMOVE_ITEM Sources ${DB4DRoot}/Sources/JS4D_oldPart.cpp)


add_library(DB4D SHARED ${Sources})


#jmo - Temporary stuff !
add_definitions(-DDB4D_AS_DLL=1)


include_directories(${ComponentsRoot}
  ${DB4DRoot}/Headers
  ${DB4DRoot}/Sources
  ${HttpServerIncludeDir}
  ${IcuIncludeDir}
  ${JsCoreIncludeDir}
  ${KernelIPCIncludeDir}
  ${KernelIncludeDir}
  ${SecurityManagerIncludeDir}
  ${ServerNetIncludeDir}
  ${XBoxRoot})


target_link_libraries(DB4D JavaScript Kernel KernelIPC ServerNet Xml)

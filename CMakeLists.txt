cmake_minimum_required (VERSION 2.6 FATAL_ERROR)

project      (cloud_annotation_tool)
#find_package (Qt5 REQUIRED)
find_package(Qt5 COMPONENTS Widgets REQUIRED)
find_package (VTK REQUIRED)
find_package (PCL 1.2 REQUIRED)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

include_directories (${PCL_INCLUDE_DIRS})
link_directories    (${PCL_LIBRARY_DIRS})
add_definitions     (${PCL_DEFINITIONS})

set (project_SOURCES   main.cpp viewer.cpp)
set (project_HEADERS   viewer.h)
set (project_FORMS     viewer.ui)
set (project_RESOURCES resources.qrc)
#set (VTK_LIBRARIES     vtkRendering vtkGraphics vtkHybrid QVTK)

#QT5_WRAP_CPP      (project_HEADERS_MOC   ${project_HEADERS})
#QT5_WRAP_UI       (project_FORMS_HEADERS ${project_FORMS})
#QT5_ADD_RESOURCES (project_RESOURCES_RCC ${project_RESOURCES})

#INCLUDE         (${QT_USE_FILE})
#ADD_DEFINITIONS (${QT_DEFINITIONS})

# ADD_EXECUTABLE (cloud_annotation_tool ${project_SOURCES} ${project_FORMS_HEADERS} ${project_HEADERS_MOC} ${project_RESOURCES_RCC})
ADD_EXECUTABLE (cloud_annotation_tool ${project_SOURCES} ${project_FORMS_HEADERS} ${project_RESOURCES_RCC})

target_link_libraries(cloud_annotation_tool Qt5::Widgets)
TARGET_LINK_LIBRARIES (cloud_annotation_tool ${PCL_LIBRARIES} ${VTK_LIBRARIES})
# TARGET_LINK_LIBRARIES (cloud_annotation_tool ${QT_LIBRARIES} ${PCL_LIBRARIES} ${VTK_LIBRARIES})
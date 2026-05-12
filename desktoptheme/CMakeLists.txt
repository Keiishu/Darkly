cmake_minimum_required(VERSION 3.16)

set(PROJECT_NAMESPACE darkly)
set(PACKAGE_INSTALL_DATADIR ${KDE_INSTALL_DATADIR}/plasma/desktoptheme)

configure_file("${CMAKE_CURRENT_SOURCE_DIR}/metadata.desktop.in" "${CMAKE_CURRENT_BINARY_DIR}/metadata.desktop" @ONLY)

install(FILES "${CMAKE_CURRENT_BINARY_DIR}/metadata.desktop" DESTINATION "${PACKAGE_INSTALL_DATADIR}/${PROJECT_NAMESPACE}")
install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/plasmarc" DESTINATION "${PACKAGE_INSTALL_DATADIR}/${PROJECT_NAMESPACE}")
install(DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/dialogs/" DESTINATION "${PACKAGE_INSTALL_DATADIR}/${PROJECT_NAMESPACE}/dialogs")

set(DARKLY_DESKTOP_THEME_WIDGETS
    background.svg
    bar_meter_horizontal.svg
    button.svg
    clock.svg
    dragger.svg
    frame.svg
    line.svgz
    lineedit.svg
    # panel-background.svg
    radiobutton.svgz
    scrollbar.svg
    slider.svg
    # tabbar.svg
    # tasks.svg
    viewitem.svg
)

foreach(widget_file IN LISTS DARKLY_DESKTOP_THEME_WIDGETS)
    install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/widgets/${widget_file}" DESTINATION "${PACKAGE_INSTALL_DATADIR}/${PROJECT_NAMESPACE}/widgets")
endforeach()

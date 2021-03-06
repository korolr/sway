include(Wayland)

WAYLAND_ADD_PROTOCOL_CLIENT(proto-client-xdg-shell
	xdg-shell.xml
	xdg-shell
)
WAYLAND_ADD_PROTOCOL_CLIENT(proto-client-desktop-shell
	desktop-shell.xml
	desktop-shell
)
WAYLAND_ADD_PROTOCOL_SERVER(proto-server-desktop-shell
	desktop-shell.xml
	desktop-shell
)

WAYLAND_ADD_PROTOCOL_CLIENT(proto-client-swaylock
	swaylock.xml
	swaylock
)
WAYLAND_ADD_PROTOCOL_SERVER(proto-server-swaylock
	swaylock.xml
	swaylock
)

WAYLAND_ADD_PROTOCOL_SERVER(proto-server-gamma-control
	gamma-control.xml
	gamma-control
)

WAYLAND_ADD_PROTOCOL_SERVER(proto-server-server-decoration
	server-decoration.xml
	server-decoration
)

add_library(sway-protocols STATIC
	${proto-client-xdg-shell}
	${proto-client-desktop-shell}
	${proto-server-desktop-shell}
	${proto-client-swaylock}
	${proto-server-swaylock}
	${proto-server-gamma-control}
	${proto-server-server-decoration}
	)

set(PROTOCOLS_INCLUDE_DIRS ${CMAKE_BINARY_DIR}/protocols PARENT_SCOPE)
INCLUDE_DIRECTORIES(${WAYLAND_INCLUDE_DIR} ${XKBCOMMON_INCLUDE_DIRS})

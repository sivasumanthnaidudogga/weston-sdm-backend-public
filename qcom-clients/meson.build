# QDCM Solid Color Tool - Wayland client to mimic QDCM TPG for calibration
# Reuses protocol headers and internal deps from weston's top-level build

qdcm_solid_color_sources = [
    'weston-qdcm-solid-color-tool.c',
    xdg_shell_client_protocol_h,
    xdg_shell_protocol_c,
    ivi_application_client_protocol_h,
    ivi_application_protocol_c,
    xdg_output_unstable_v1_client_protocol_h,
    xdg_output_unstable_v1_protocol_c,
]

qdcm_solid_color_deps = [
    dep_wayland_client,
    dep_libshared,
    dep_libm,
]

foreach depname : [ 'egl', 'wayland-egl', 'glesv2', 'wayland-cursor' ]
    dep = dependency(depname, required: false)
    if not dep.found()
        error('weston-simple-qdcm-solid-color requires @0@ which was not found.'.format(depname))
    endif
    qdcm_solid_color_deps += dep
endforeach

executable(
    'weston-simple-qdcm-solid-color',
    qdcm_solid_color_sources,
    include_directories: common_inc,
    dependencies: qdcm_solid_color_deps,
    install: true,
    c_args: ['-fstack-protector-all'],
)
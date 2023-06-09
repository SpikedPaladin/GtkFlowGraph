lib_deps = [
    dependency('gtk4')
]

lib_sources = files(
    'css-loader.vala',
    'minimap.vala',
    'node.vala',
    'node-view.vala',
    'rubberband.vala',
    'sink.vala',
    'socket.vala',
    'source.vala',
    
    'renderers/connection-renderer.vala',
    'renderers/socket-renderer.vala',
)

install_data(
    'deps.in',
    
    rename: lib_name + '.deps',
    install_dir: get_option('datadir') / 'vala' / 'vapi'
)

lib = library(
    lib_name,
    
    lib_resources,
    lib_sources,
    dependencies: lib_deps,
    vala_args: [ '--gresourcesdir=data/' ],
    install: true,
    install_dir: [true, true, true]
)

pkg.generate(
    name: meson.project_name(),
    description: 'Flow Graph library for Gtk4',
    
    libraries: lib,
    version: meson.project_version(),
    subdirs: lib_name,
    filebase: lib_name,
    requires: ['gtk4']
)

lib_dependency = declare_dependency(
    link_with: lib,
    include_directories: include_directories('.')
)

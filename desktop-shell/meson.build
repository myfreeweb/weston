if get_option('shell-desktop')
	config_h.set_quoted('WESTON_SHELL_CLIENT', get_option('desktop-shell-client-default'))

	srcs_shell_desktop = [
		'shell.c',
		'exposay.c',
		'input-panel.c',
		'../shared/matrix.c',
		weston_desktop_shell_server_protocol_h,
		weston_desktop_shell_protocol_c,
		input_method_unstable_v1_server_protocol_h,
		input_method_unstable_v1_protocol_c,
	]
	deps_shell_desktop = [
		dep_libshared,
		dep_lib_desktop,
		dep_libweston,
	]
	plugin_shell_desktop = shared_library(
		'desktop-shell',
		srcs_shell_desktop,
		include_directories: include_directories('..', '../shared'),
		dependencies: deps_shell_desktop,
		name_prefix: '',
		install: true,
		install_dir: dir_module_weston
	)
	install_headers(
		'desktop-shell-api.h',
		subdir: dir_include_libweston
	)
	env_modmap += 'desktop-shell.so=@0@;'.format(plugin_shell_desktop.full_path())
endif

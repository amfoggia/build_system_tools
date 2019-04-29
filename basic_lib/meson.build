project('libbasic', 'cpp', default_options: ['cpp_std=c++17'], version: ['0.1.0'])

add_project_arguments(language: 'cpp')

conf_data = configuration_data()
conf_data.set_quoted('version', meson.project_version())
conf_data.set('shared_lib', get_option('shared_lib'))
conf_data.set('static_lib', get_option('static_lib'))
configure_file(input: './meson_config.h.in',
	       output: 'meson_config.h',
	       configuration: conf_data)

inc = include_directories('.', './include')

subdir('./src')

src = [sum_range, mult_range, dot, abs]

if get_option('shared_lib') == true
   libtype = 'shared_library'
else
   libtype = 'static_library'
endif

libbasic = build_target('basic',
                        src,
	            	name_prefix: 'lib',
		    	name_suffix: [],
		    	cpp_args: ['-O2', '-Wall'],
			include_directories: inc,
			target_type: libtype,
			install: true)
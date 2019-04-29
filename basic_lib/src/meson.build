sum_range = files('sum_range.cpp')
mult_range = files('mult_range.cpp')
dot = files('dot.cpp')
abs = files('abs.cpp')

src = [sum_range, mult_range, dot, abs]

libbasic = build_target('basic',
                        src,
	            	name_prefix: 'lib',
		    	name_suffix: [],
		    	cpp_args: ['-O2', '-Wall'],
			include_directories: inc,
			target_type: libtype,
			install: true)
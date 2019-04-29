project('basic_lib', 'cpp', default_options: ['cpp_std=c++17'], version: ['0.1.0'])

inc = include_directories('./basic_lib/include')

src = [sum_range, mult_range, dot, abs]

basic_lib = library('basiclib',
	            src,
	            name_prefix: 'lib',
		    name_suffix: ['.so', '.a'],
		    cpp_args: ['-O2', '-Wall'])
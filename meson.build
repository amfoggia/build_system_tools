project('my_exec', 'cpp', default_options: ['cpp_std=c++17'], version: '0.0.1')

cool_dep = dependency('cool')

exec_main = executable('main.x',
                      ['main.cpp'],
                      dependencies: [cool_dep])
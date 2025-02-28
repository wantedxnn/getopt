project(
  'getopt',
  'c',
  version: '0.95',
  license : ['ISC', 'BSD-3-Clause'],
  meson_version: '>= 0.55',
  default_options: [
    'warning_level=1',
  ],
)

compiler = meson.get_compiler('c')

c_args = []

if compiler.get_id() == 'msvc'
  c_args += [
    '-D_CRT_SECURE_NO_WARNINGS',
  ]

  if get_option('default_library') == 'shared'
    c_args += [
      '-DBUILDING_GETOPT_DLL',
      '-DGETOPT_SHARED_LIB',
    ]
  endif
endif

getopt_lib = library(
  'getopt',
  'src/getopt.c',
  include_directories: include_directories(
    'src',
  ),
  c_args: c_args,
)

getopt_dep = declare_dependency(
  link_with: getopt_lib,
  include_directories: include_directories(
    'src',
  ),
)

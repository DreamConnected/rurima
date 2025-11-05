# Rurima includes.
rurima_includes = include_directories(
    'include',
    'ruri')

## libcatsh
libcatsh_include_dir = include_directories('catsh/src/include')

libcatsh_sources = [
  'catsh/src/catsh.c',
]

libcatsh = library('catsh',
  libcatsh_sources,
  include_directories: libcatsh_include_dir,
  install: true,
  version: '0.5.0',
  soversion: '1',
)

pkgconfig.generate(libcatsh,
  name: 'libcatsh',
  description: 'C ATSH library',
  version: '0.5.0',
)

libcatsh_dep = declare_dependency(
  link_with: libcatsh,
  include_directories: libcatsh_include_dir,
)

install_headers('catsh/src/include/catsh.h', subdir: 'catsh')

## libcprintf
libcprintf_include_dir = include_directories('ruri/src/include')

libcprintf_sources = [
  'ruri/src/cprintf.c',
]

libcprintf = library('cprintf',
  libcprintf_sources,
  include_directories: libcprintf_include_dir,
  install: true,
  version: '0.2.1',
  soversion: '1',
)

pkgconfig.generate(libcprintf,
  name: 'libcprintf',
  description: 'C formatted print library',
  version: '0.2.1',
)

libcprintf_dep = declare_dependency(
  link_with: libcprintf,
  include_directories: libcprintf_include_dir,
)

install_headers('ruri/src/include/cprintf.h', subdir: 'cprintf')


## libruri
libruri_include_dir = include_directories(
    'ruri/src/include',
    'ruri/src/easteregg/include')

libruri_sources = [
    'ruri/src/easteregg/action.c',
    'ruri/src/easteregg/layer.c',
    'ruri/src/easteregg/nekofeng.c',
    'ruri/src/easteregg/typewriter.c',
    'ruri/src/caplist.c',
    'ruri/src/cgroup.c',
    'ruri/src/chroot.c',
    'ruri/src/config.c',
    'ruri/src/elf-magic.c',
    'ruri/src/info.c',
    'ruri/src/k2v.c',
    'ruri/src/mount.c',
    'ruri/src/passwd.c',
    'ruri/src/ps.c',
    'ruri/src/rootless.c',
    'ruri/src/ruri.c',
    'ruri/src/rurienv.c',
    'ruri/src/rurifetch.c',
    'ruri/src/seccomp.c',
    'ruri/src/signal.c',
    'ruri/src/umount.c',
    'ruri/src/unshare.c'
]

libruri = library('ruri',
  libruri_sources,
  include_directories: libruri_include_dir,
  dependencies: [
    libcprintf_dep,
    libcatsh_dep,
    libruri_dependencies,
  ],
  install: true,
  version: libruri_version,
  soversion: '1',
)

pkgconfig.generate(
    libruri,
    name: 'libruri',
    description: 'RURI library',
    version: libruri_version,
    requires: ['libcprintf', 'libcatsh', 'libcap', 'libseccomp'],
)

libruri_dep = declare_dependency(
  link_with: libruri,
  include_directories: libruri_include_dir,
  dependencies: [
    libcprintf_dep,
    libcatsh_dep,
    libruri_dependencies,
  ],
)

install_headers('ruri/src/include/ruri.h', subdir: 'ruri')

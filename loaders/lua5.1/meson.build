if enable_lua == 'auto'
  lua_dep = dependency('lua5.1', version: '>= 5.1', required: false)
  if not lua_dep.found()
    lua_dep = dependency('luajit', version: '>= 2.0', required: false)
  endif
elif enable_lua == 'lua51'
  lua_dep = dependency('lua5.1', version: '>= 5.1')
elif enable_lua == 'luajit'
  lua_dep = dependency('luajit', version: '>= 2.0')
endif

if lua_dep.found()
  lua_built = true
  subdir('resources')

  shared_module('lua51loader',
    sources: [
      'peas-lua-internal.c',
      'peas-plugin-loader-lua.c',
      'peas-lua-utils.c',
      peas_lua_resources,
    ],
    dependencies: [
      lua_dep,
      libgio_dep,
      libgobject_introspection_dep,
    ],
    install: true,
    install_dir: peasloaderdir
  )
endif

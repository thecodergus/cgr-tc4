# Projeto de exemplo para uso do GenICam com C++ e Python
project('Aplicação', 'cpp', default_options : ['cpp_std=c++20'])

# Inicia as flags de compilação como um vetor vazio
cpp_args = []

# Adiciona flags de compilação para o GCC e Clang
cc = meson.get_compiler('cpp')
if cc.get_id() == 'g++' or cc.get_id() == 'clang++'
  cpp_args += '-Wno-deprecated'
endif

# Importa as dependências e pastas de cabeçalho
inc = include_directories('include', '/usr/local/include')

compiler = meson.get_compiler('cpp')

# Local para importar as dependencias
openGL_dep = dependency('gl')
glew_dep = dependency('glew', required: false)
gluL_dep = dependency('glu')
glut_dep = dependency('glut', required: false)
thread_dep = dependency('threads')
freeimage_dep = compiler.find_library('freeimage', dirs: '/usr/lib/x86_64-linux-gnu/')
math_dep = cc.find_library('m', required : false)



libsPath = '/usr/lib/x86_64-linux-gnu/'
if not glut_dep.found()
  glut_dep = compiler.find_library('glut', dirs: libsPath)
endif
if math_dep.found()
  add_project_link_arguments('-lm', language : 'cpp')
endif


# Importa os arquivos de código fonte
app_src = files(
  'src/CreateOBJ.cpp',
  'src/OBJModel.cpp'
)

# Local para importar as dependencias

# Aplicação Central
executable('main', 
    sources : [
      app_src
    ], 
    include_directories : inc, 
    dependencies: [
      openGL_dep, 
      glew_dep,
      glut_dep, 
      gluL_dep, 
      thread_dep,
      math_dep,
      freeimage_dep
    ],
    install: true, 
    cpp_args : cpp_args
  )

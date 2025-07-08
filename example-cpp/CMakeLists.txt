#  ██████╗██████╗ ██████╗ 
# ██╔════╝██╔══██╗██╔══██╗
# ██║     ██████╔╝██████╔╝
# ██║     ██╔═══╝ ██╔═══╝ 
# ╚██████╗██║     ██║     
#  ╚═════╝╚═╝     ╚═╝     
                        

set(cpp_src hello.cpp)

add_executable(example-hello ${cpp_src})

install(TARGETS example-hello)
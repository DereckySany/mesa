# Copyright © 2017 Broadcom
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

kmsro_c_args = []
if with_gallium_etnaviv
  kmsro_c_args += '-DGALLIUM_ETNAVIV'
endif
if with_gallium_lima
  kmsro_c_args += '-DGALLIUM_LIMA'
endif
if with_gallium_v3d
  kmsro_c_args += '-DGALLIUM_V3D'
endif
if with_gallium_vc4
  kmsro_c_args += '-DGALLIUM_VC4'
endif
if with_gallium_freedreno
  kmsro_c_args += '-DGALLIUM_FREEDRENO'
endif
if with_gallium_panfrost
  kmsro_c_args += '-DGALLIUM_PANFROST'
endif
if with_gallium_asahi
  kmsro_c_args += '-DGALLIUM_ASAHI'
endif

libkmsrowinsys = static_library(
  'kmsrowinsys',
  files('kmsro_drm_winsys.c'),
  include_directories : [
    inc_src, inc_include,
    inc_gallium, inc_gallium_aux, inc_gallium_winsys,
  ],
  c_args : [kmsro_c_args],
  gnu_symbol_visibility : 'hidden',
  dependencies: [dep_libdrm, dep_valgrind],
)

driver_kmsro = declare_dependency(
  compile_args : '-DGALLIUM_KMSRO',
  link_with : libkmsrowinsys,
)

# Copyright 2015 Pants project contributors (see CONTRIBUTORS.md).
# Licensed under the Apache License, Version 2.0 (see LICENSE).

python_library(
  name='binary_util',
  sources=['binary_util.py'],
  dependencies=[
    '3rdparty/python/twitter/commons:twitter.common.collections',
    '3rdparty/python:six',
    'src/python/pants/base:exceptions',
    'src/python/pants/option',
    'src/python/pants/subsystem',
    'src/python/pants/util:contextutil',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name='thrift_util',
  sources=['thrift_binary.py'],
  dependencies=[
    ':binary_util',
    'src/python/pants/subsystem',
    'src/python/pants/util:memo',
  ],
)

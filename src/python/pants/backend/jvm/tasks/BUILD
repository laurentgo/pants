# Copyright 2014 Pants project contributors (see CONTRIBUTORS.md).
# Licensed under the Apache License, Version 2.0 (see LICENSE).

python_library(
  name = 'all',
  dependencies = [
    ':benchmark_run',
    ':binary_create',
    ':bootstrap_jvm_tools',
    ':bundle_create',
    ':check_published_deps',
    ':checkstyle',
    ':detect_duplicates',
    ':ivy_imports',
    ':ivy_resolve',
    ':ivy_task_mixin',
    ':jar_create',
    ':jar_publish',
    ':javadoc_gen',
    ':junit_run',
    ':jvm_binary_task',
    ':jvm_platform_analysis',
    ':jvm_run',
    ':jvm_task',
    ':jvm_tool_task_mixin',
    ':jvmdoc_gen',
    ':nailgun_task',
    ':prepare_resources',
    ':prepare_services',
    ':resources_task',
    ':scala_repl',
    ':scaladoc_gen',
    ':scalastyle',
    ':unpack_jars',
    'src/python/pants/backend/jvm/tasks/jvm_compile:all',
  ],
)

python_library(
  name = 'benchmark_run',
  sources = ['benchmark_run.py'],
  dependencies = [
    ':jvm_task',
    ':jvm_tool_task_mixin',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/base:workunit',
    'src/python/pants/java:util',
  ],
)

python_library(
  name = 'binary_create',
  sources = ['binary_create.py'],
  dependencies = [
    ':jvm_binary_task',
    'src/python/pants/base:build_environment',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'bootstrap_jvm_tools',
  sources = ['bootstrap_jvm_tools.py'],
  dependencies = [
    ':ivy_task_mixin',
    ':jar_task',
    'src/python/pants/base:cache_manager',
    'src/python/pants/base:exceptions',
    'src/python/pants/base:workunit',
    'src/python/pants/ivy',
    'src/python/pants/java:executor',
    'src/python/pants/java:util',
    'src/python/pants/java/jar:shader',
    'src/python/pants/backend/jvm/subsystems:jvm_tool_mixin',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'bundle_create',
  sources = ['bundle_create.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    ':jvm_binary_task',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:exceptions',
    'src/python/pants/fs',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'check_published_deps',
  sources = ['check_published_deps.py'],
  dependencies = [
    ':jar_publish',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/backend/core/tasks:console_task',
  ],
)

python_library(
  name = 'checkstyle',
  sources = ['checkstyle.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    ':nailgun_task',
    'src/python/pants/base:exceptions',
    'src/python/pants/java/jar:shader',
    'src/python/pants/option',
    'src/python/pants/process',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'classpath_util',
  sources = ['classpath_util.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
  ],
)

python_library(
  name = 'classpath_products',
  sources = ['classpath_products.py'],
  dependencies = [
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:exceptions',
    'src/python/pants/goal:products',
  ],
)

python_library(
  name = 'detect_duplicates',
  sources = ['detect_duplicates.py'],
  dependencies = [
    ':jvm_binary_task',
    # TODO(pl): Use twitter.common.lang instead, but for the to_bytes helper, twitter.commons
    # needs to be updated so the standard compatibility helpers act like the ones in pex
    '3rdparty/python:pex',
    'src/python/pants/base:exceptions',
    'src/python/pants/java/jar:manifest',
    'src/python/pants/util:contextutil',
  ],
)

python_library(
  name = 'ivy_imports',
  sources = ['ivy_imports.py'],
  dependencies = [
    ':ivy_task_mixin',
    ':nailgun_task',
  ],
)

python_library(
  name = 'ivy_resolve',
  sources = ['ivy_resolve.py'],
  dependencies = [
    ':classpath_products',
    ':ivy_task_mixin',
    ':nailgun_task',
    'src/python/pants/backend/jvm:ivy_utils',
    'src/python/pants/base:cache_manager',
    'src/python/pants/binaries:binary_util',
    'src/python/pants/goal:products',
    'src/python/pants/ivy',
    'src/python/pants/subsystem',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'ivy_task_mixin',
  sources = ['ivy_task_mixin.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    'src/python/pants/backend/jvm:ivy_utils',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/base:cache_manager',
    'src/python/pants/base:exceptions',
    'src/python/pants/base:fingerprint_strategy',
    'src/python/pants/ivy',
    'src/python/pants/java:util',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'jar_create',
  sources = ['jar_create.py'],
  dependencies = [
    ':jar_task',
    'src/python/pants/base:exceptions',
    'src/python/pants/base:workunit',
    'src/python/pants/backend/jvm/targets:jvm',
  ],
)

python_library(
  name = 'jar_publish',
  sources = ['jar_publish.py'],
  resources = globs('templates/jar_publish/*.mustache', 'templates/ivy_resolve/*.mustache'),
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    '3rdparty/python/twitter/commons:twitter.common.config',
    ':jar_task',
    'src/python/pants/backend/core/tasks:scm_publish',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/backend/jvm/targets:scala',
    'src/python/pants/backend/jvm:ivy_utils',
    'src/python/pants/backend/jvm:ossrh_publication_metadata',
    'src/python/pants/base:address',
    'src/python/pants/base:address_lookup_error',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:build_file',
    'src/python/pants/base:build_file_parser',
    'src/python/pants/base:build_graph',
    'src/python/pants/base:exceptions',
    'src/python/pants/base:generator',
    'src/python/pants/base:target',
    'src/python/pants/ivy',
    'src/python/pants/option',
    'src/python/pants/scm',
    'src/python/pants/util:dirutil',
    'src/python/pants/util:strutil',
  ],
)

python_library(
  name = 'jar_task',
  sources = ['jar_task.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    '3rdparty/python:six',
    ':nailgun_task',
    'src/python/pants/backend/jvm/subsystems:jar_tool',
    'src/python/pants/backend/jvm/targets:java',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:exceptions',
    'src/python/pants/binaries:binary_util',
    'src/python/pants/java/jar:manifest',
    'src/python/pants/util:contextutil',
    'src/python/pants/util:meta',
  ],
)

python_library(
  name = 'javadoc_gen',
  sources = ['javadoc_gen.py'],
  dependencies = [
    ':jvmdoc_gen',
    'src/python/pants/java/distribution',
    'src/python/pants/java:executor',
    'src/python/pants/util:memo',
  ],
)

python_library(
  name = 'junit_run',
  sources = ['junit_run.py'],
  dependencies = [
    '3rdparty/python:six',
    ':jvm_task',
    ':jvm_tool_task_mixin',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/backend/jvm/targets:java',
    'src/python/pants/base:build_environment',
    'src/python/pants/base:workunit',
    'src/python/pants/binaries:binary_util',
    'src/python/pants/java/jar:shader',
    'src/python/pants/java:util',
    'src/python/pants/util:contextutil',
    'src/python/pants/util:dirutil',
    'src/python/pants/util:xml_parser',
  ],
)

python_library(
  name = 'jvm_binary_task',
  sources = ['jvm_binary_task.py'],
  dependencies = [
    ':jar_task',
    '3rdparty/python/twitter/commons:twitter.common.collections',
    'src/python/pants/backend/jvm/targets:jvm',
  ],
)

python_library(
  name = 'jvm_platform_analysis',
  sources = ['jvm_platform_analysis.py'],
  dependencies = [
    '3rdparty/python:ansicolors',
    'src/python/pants/backend/core/tasks:console_task',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/base:exceptions',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/util:memo',
  ]
)

python_library(
  name = 'jvm_run',
  sources = ['jvm_run.py'],
  dependencies = [
    ':jvm_task',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/base:workunit',
    'src/python/pants/fs',
    'src/python/pants/java:executor',
    'src/python/pants/java:util',
    'src/python/pants/util:dirutil',
    'src/python/pants/util:strutil',
  ],
)

python_library(
  name = 'jvm_task',
  sources = ['jvm_task.py'],
  dependencies = [
    ':classpath_util',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/backend/jvm/subsystems:jvm',
  ],
)

python_library(
  name = 'jvm_tool_task_mixin',
  sources = ['jvm_tool_task_mixin.py'],
  dependencies = [
    'src/python/pants/backend/jvm/subsystems:jvm_tool_mixin',
    'src/python/pants/base:exceptions',
  ],
)

python_library(
  name = 'jvmdoc_gen',
  sources = ['jvmdoc_gen.py'],
  dependencies = [
    ':jvm_task',
    'src/python/pants/base:exceptions',
    'src/python/pants/binaries:binary_util',
    'src/python/pants/util:dirutil',\
  ],
)

python_library(
  name = 'nailgun_task',
  sources = ['nailgun_task.py'],
  dependencies = [
    ':jvm_tool_task_mixin',
    'src/python/pants/base:exceptions',
    'src/python/pants/java:executor',
    'src/python/pants/java:nailgun_executor',
    'src/python/pants/java/distribution:distribution',
    'src/python/pants/java:util',
    'src/python/pants/backend/core/tasks:task',
  ],
)

python_library(
  name = 'prepare_resources',
  sources = ['prepare_resources.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.collections',
    ':resources_task',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/base:build_environment',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'prepare_services',
  sources = ['prepare_services.py'],
  dependencies = [
    ':resources_task',
    'src/python/pants/backend/jvm/targets:jvm',
    'src/python/pants/base:fingerprint_strategy',
    'src/python/pants/base:payload_field',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'resources_task',
  sources = ['resources_task.py'],
  dependencies = [
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/base:build_environment',
    'src/python/pants/goal:products',
    'src/python/pants/option',
    'src/python/pants/util:dirutil',
  ],
)

python_library(
  name = 'scala_repl',
  sources = ['scala_repl.py'],
  dependencies = [
    ':jvm_task',
    ':jvm_tool_task_mixin',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/base:workunit',
    'src/python/pants/console:stty_utils',
    'src/python/pants/java:util',
    'src/python/pants/util:strutil',
  ],
)

python_library(
  name = 'scaladoc_gen',
  sources = ['scaladoc_gen.py'],
  dependencies = [
    ':jvmdoc_gen',
    'src/python/pants/backend/jvm/subsystems:scala_platform',
    'src/python/pants/java:executor',
    'src/python/pants/util:memo',
  ],
)

python_library(
  name = 'scalastyle',
  sources = ['scalastyle.py'],
  dependencies = [
    ':nailgun_task',
    'src/python/pants/base:exceptions',
    'src/python/pants/base:target',
    'src/python/pants/process',
    'src/python/pants/util:dirutil'
  ],
)

python_library(
  name = 'unpack_jars',
  sources = ['unpack_jars.py'],
  dependencies = [
    '3rdparty/python/twitter/commons:twitter.common.dirutil',
    'src/python/pants/backend/core/tasks:task',
    'src/python/pants/backend/jvm/targets:jvm',
  ]
)

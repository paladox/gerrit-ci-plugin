include_defs('//bucklets/gerrit_plugin.bucklet')

gerrit_plugin(
  name = 'ci',
  srcs = glob(['src/main/java/**/*.java']),
  resources = glob(['src/main/**/*']),
  manifest_entries = [
    'Gerrit-PluginName: ci',
    'Gerrit-Module: com.googlesource.gerrit.plugins.ci.GlobalModule',
    'Gerrit-SshModule: com.googlesource.gerrit.plugins.ci.SshModule',
    'Implementation-Title: CI plugin',
    'Implementation-URL: https://gerrit-review.googlesource.com/#/admin/projects/plugins/ci',
  ],
  provided_deps = [
    '//lib/commons:dbcp',
    '//lib:gson',
  ]
)

java_test(
  name = 'ci_tests',
  srcs = glob(['src/test/java/**/*IT.java']),
  labels = ['ci-plugin'],
  source_under_test = [':ci__plugin'],
  deps = GERRIT_PLUGIN_API + GERRIT_TESTS + [
    ':ci__plugin',
  ],
)

java_library(
  name = 'classpath',
  deps = GERRIT_PLUGIN_API + GERRIT_TESTS + [
    ':ci__plugin'
  ],
)
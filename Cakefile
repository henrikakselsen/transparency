{exec} = require 'child_process'

task 'build', 'compile and uglify transparency', (options) ->
  exec(
    [
      "coffee -o lib -c src/jquery.transparency.coffee"
      "coffee -o browser/spec spec/*.coffee"
      "uglifyjs lib/jquery.transparency.js > lib/jquery.transparency.min.js"
    ].join(' && '), (err, stdout, stderr) ->
      if err then console.log stderr.trim()
  )

task 'perf', 'run perf tests', (options) ->
  invoke 'build'
  exec(
    [
      "coffee -o perf/js -c perf/src/*.coffee"
    ].join(' && '), (err, stdout, stderr) ->
      console.log stdout.trim() if stdout
      console.log stderr.trim() if err
  )
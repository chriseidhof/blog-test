require 'rubygems'
require 'middleman-aws'

desc 'Deploy to S3 and invalidate Cloudfront after a Git commit/push'
task :deploy do
  puts '## Syncing to S3...'
  system "bundle exec middleman s3_sync"
  # puts '## Invalidating cloudfront...'
  # system "#{aws_env}  bundle exec middleman invalidate"
  puts '## Deploy complete.'
end

desc 'One step clobber, build, deploy'
task :publish => ["mm:clobber", "mm:build", :deploy] do
end

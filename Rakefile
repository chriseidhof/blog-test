require 'rubygems'
require 'middleman-aws'

# Rake::Task['mm:deploy'].clear

desc 'Deploy to S3 and invalidate Cloudfront after a Git commit/push'
task :deploy do
  puts '## Deploy starting...'
  credentials!
  aws_env = "AWS_ACCESS_KEY=#{credentials['access_key_id']} AWS_SECRET=#{credentials['secret_access_key']}"
  puts '## Syncing to S3...'
  system "#{aws_env} bundle exec middleman s3_sync"
  # puts '## Invalidating cloudfront...'
  # system "#{aws_env}  bundle exec middleman invalidate"
  puts '## Deploy complete.'
end

desc 'One step clobber, build, deploy'
task :publish => ["mm:clobber", "mm:build", :deploy] do
end

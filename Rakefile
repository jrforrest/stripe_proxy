namespace :db do
  desc "Update db schema"
  task :migrate, [:version] do |t, args|
    require 'sequel'
    Sequel.extension :migration
    db = Sequel.connect(ENV.fetch('DATABASE_URL'))
    if args[:version]
      puts "Migration to version: #{args[:version]}"
      Sequel::Migrator.run(db, 'migrations', target: args[:version].to_i)
    else
      puts "Migrating to latest"
      Sequel::Migrator.run(db, 'migrations')
    end
  end
end

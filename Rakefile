namespace :greeting do
    desc 'outputs hello to the terminal'
    task :hello do
      puts "hello from Rake!"
    end

    desc 'outputs hola to terminal'
    task :hola do
      puts "hola de Rake!"
    end
  end

desc 'sets dependency to environment file'
task :environment do
  require_relative './config/environment'
end

  namespace :db do
    desc 'migrate changes to your database'
    task :migrate => :environment do
      # This creates a task dependency.
      #Since our Student.create_table code would require
      #access to the config/environment.rb file
      #(which is where the student class and database are loaded),
      #we need to give our task access to this file.
      #In order to do that, we need to define yet another
      #Rake task that we can tell to run before the migrate task is run.
      Student.create_table
    end

    desc 'seeds db with demo data'
    task :seed do
      require_relative './db/seeds.rb'
    end
end

desc 'drop into pry console'
task :console => :environment do
  Pry.start
end

require 'rubygems'

require 'debian/build'
include Debian::Build

require 'debian/build/config'

namespace "package" do
  Package.new(:"libeventmachine-ruby") do |t|
    t.version = '0.12.10'
    t.debian_increment = 1

    t.source_provider = DebianTarballProvider
  end

  namespace "libeventmachine-ruby:source:update" do
    desc "Update source tarball with current gem sources"
    task :gem do
      name = "libeventmachine-ruby"
      version="0.12.10"

      tmp_dir="/tmp/#{name}.gem"
      sources_dir="#{tmp_dir}/#{name}-#{version}"

      rm_rf tmp_dir
      mkdir_p sources_dir

      sh "gem unpack --target=#{sources_dir} eventmachine"
      sh "tar -czf '#{name}-#{version}.tgz' -C #{tmp_dir} ."
      sh "dch --newversion '#{version}-1' 'New upstream release'"
    end
  end

end


require 'debian/build/tasks'


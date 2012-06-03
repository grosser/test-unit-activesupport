# -*- coding: utf-8; mode: ruby -*-
#
# Copyright (C) 2012  Kouhei Sutou <kou@clear-code.com>
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA

require "pathname"

require "./lib/test/unit/active_support/version"

require "rubygems"
require "rubygems/package_task"
require "yard"
require 'bundler/gem_helper'
require "packnga"

base_dir = File.join(File.dirname(__FILE__))

helper = Bundler::GemHelper.new(base_dir)
helper.install
spec = helper.gemspec

Gem::PackageTask.new(spec) do |pkg|
  pkg.need_tar_gz = true
end

document_task = Packnga::DocumentTask.new(spec) do |task|
end

Packnga::ReleaseTask.new(spec) do |task|
end

desc "Tag the current revision."
task :tag do
  sh("git tag -a #{version} -m 'release #{version}!!!'")
end
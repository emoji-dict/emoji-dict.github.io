require "json"
require "erb"

module Emoji
  class Symbol < Struct.new(:symbol)
    def name
      symbol.gsub(":", "")
    end

    def to_s
      symbol
    end
  end
end

module Emoji
  class Slang < Struct.new(:symbols, :definitions)
    def self.from_json(json)
      symbols = json.fetch("emoji").split(/(:\w+:)/).reject(&:empty?)
      symbols = symbols.map { |s| Symbol.new s }
      definitions = Array(json.fetch("def"))
      new symbols, definitions
    end
  end
end

desc "build emoji-dict"
task :build do
  @slangs = Dir["dict/*.json"].map do |f|
    json = File.open(f) { |ff| JSON.load ff }
    Emoji::Slang.from_json(json)
  end

  html = ERB.new(File.read("index.html.erb")).result binding
  File.write("index.html", html)
end

desc "create a new emoji slang by passing the EMOJI and DEF environment variable"
task :new do
  emoji = ENV.fetch("EMOJI")
  definition = ENV.fetch("DEF")

  json = JSON.pretty_generate("emoji" => emoji, "def" => definition)
  File.write("dict/#{emoji}.json", json)
end

# modified slightly from: 
# http://www.codeography.com/2009/04/11/create-a-new-post-in-jekyll.html
desc "Creates a new _posts file using TITLE='the title' and today's date. JEKYLL_EXT=markdown by default"
task :post do
  ext = ENV['JEKYLL_EXT'] || "markdown"
  unless title = ENV['TITLE'] || ARGV.pop
    puts "USAGE: rake post TITLE='the post title'"
    exit(1)
  end
  post_title = "#{Date.today.strftime('%Y-%m-%d')}-#{title.downcase.gsub(/[^\w]+/, '-')}"
  post_file = File.join(File.dirname(__FILE__), '_posts', "#{post_title}.#{ext}")
  File.open(post_file, "w") do |f|
    f << <<-EOS.gsub(/^    /, '')
    ---
    layout: blog
    title: #{title}
    ---

    EOS
  end
  if (ENV['EDITOR'])
     `#{ENV['EDITOR']} #{post_file}`
  end
end

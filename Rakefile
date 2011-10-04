require 'bundler'
Bundler.require

desc "Run the jekyll server"
task :jekyll => :frontmatter do
  sh 'jekyll --server --auto --safe --pygments'
end

desc "Build the YAML frontmatter for each post"
task :frontmatter do
  Dir[ '_posts/*.md' ].each { |post| Post.new( post ).update! }
end

desc "Create a new post"
task :post do
  require 'date'
  post = shell.ask 'Post title: '
  date = DateTime.now.strftime '%Y-%m-%d'
  File.open "_posts/#{param post, date}.md", 'w+' do |f|
    d = <<EOS
---

* No frontmatter yet. After committing your post, run *rake frontmatter* to generate this section.

---

# #{post}

A short description about the post goes here.

## New Section

Some more text. Happy posting!
EOS
    f << d
  end
end

def param( post, date )
  "#{date} #{post.downcase}".gsub( /\W+/, '-' ).gsub( /^\W|\W$/, '' )
end

def shell
  @shell ||= HighLine.new
end

class Post  
  LAYOUT = /^(?:---.*---)?(.*)$/imx
  
  def initialize( filename )
    @filename = filename
  end
  def file
    @file ||= IO.read @filename
  end
  def body
    @body ||= file[ LAYOUT, 1 ]
  end
  def markup
    @markup ||= RDiscount.new( body ).to_html
  end
  def layout
    'post'
  end
  def title
    Nokogiri::HTML( markup ).xpath( '//h1' ).first.text
  end
  def excerpt
    Nokogiri::HTML( markup ).xpath( '//p' ).first.text
  end
  def authors
    log.map( &:author ).map { |a| { 'name' => a.name, 'email' => a.email } }.uniq
  end
  def log
    @log ||= git.log( 50 ).object( @filename )
  end  
  def git
    @git ||= Git.open '.'
  end

  def update!
    # automatically update yaml frontmatter
    head = { }
    head[ 'layout'  ] = layout
    head[ 'title'   ] = title
    head[ 'excerpt' ] = excerpt
    head[ 'authors' ] = authors
    
    # concat it with our body and write out
    File.open @filename, 'w+' do |f|
      p = <<EOS
#{head.to_yaml}
---

#{body.strip}
EOS
      f << p
    end
    
    puts "Updated #{@filename}"
  end
end

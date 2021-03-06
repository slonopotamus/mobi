<a href="https://codeclimate.com/github/jkongie/mobi"><img src="https://codeclimate.com/github/jkongie/mobi/badges/gpa.svg" /></a>

# mobi

A Ruby Gem that reads MOBI metadata.

## Ruby

Compatible up to ruby 2.0.0p0.

I haven't tested beyond that version, but it should work.

## Installation

`gem install mobi`

## Usage

Creating a Mobi::Metadata object

```ruby
Mobi::Metadata.new(File.open('/path/to/file.mobi'))
```

A handy convenience method to do the exact same thing

```ruby
Mobi.metadata File.open('/path/to/file.mobi')
```

Getting metadata information is as simple as:

```ruby
metadata = Mobi.metadata File.open('/path/to/fellowship_of_the_ring.mobi')
#=> #<Mobi::Metadata>
metadata.author
#=> "J.R.R. Tolkien"
```

Supported metadata options are:

* asin
* author
* contributor
* description
* imprint
* isbn
* publisher
* published_at
* review
* rights
* source
* subject
* subject_code
* title
* type
* version

You can also drill down and get the PalmDOC and MOBI header details:

```ruby
palm_doc_header = metadata.palm_doc_header
#=> #<Mobi::Header::PalmDocHeader>
palm_doc_header.raw_compression_type
#=> 2
palm_doc_header.compression_type
#=> "PalmDOC"

mobi_header = metadata.mobi_header
#=> #<Mobi::Header::MobiHeader>
mobi_header.raw_mobi_type
#=> 2
mobi_header.mobi_type
#=> "MOBIpocket Book"
```

See the source for more methods.

## Thanks

* Calibre open source project. I ripped off the idea of a Stream Slicer and got a better understanding of MOBI files from their code base. Check them out at http://calibre-ebook.com

## Contributing to mobi

* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
* Fork the project
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

## Copyright

Copyright (c) 2011 jkongie. See LICENSE.txt for further details.


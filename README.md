# has_full_name

Forked from frozen repo [basecamp/name_of_person](https://github.com/basecamp/name_of_person)

Presenting names for English-language applications where a basic model of first and last name(s) combined is sufficient. This approach is not meant to cover all possible naming cases, deal with other languages, or even titulations. Just the basics.

## Examples

```ruby
# Relies on Person having a schema with first_name and last_name columns.
class Person < ApplicationRecord
  has_full_name
end

# Saves a new record using { first_name: "David", last_name: "Heinemeier Hansson" }
person = Person.create! name: "David Heinemeier Hansson"

person.name.full        # => "David Heinemeier Hansson"
person.name.first       # => "David"
person.name.last        # => "Heinemeier Hansson"
person.name.initials    # => "DHH"
person.name.familiar    # => "David H."
person.name.abbreviated # => "D. Heinemeier Hansson"
person.name.sorted      # => "Heinemeier Hansson, David"
person.name.mentionable # => "davidh"
person.name.possessive  # => "David Heinemeier Hansson's"
person.name.possessive(:first)  # => "David's"
person.name.possessive(:last)  # => "Hansson's"
person.name.possessive(:initials)  # => "DHH's"
person.name.possessive(:sorted)  # => "Heinemeier Hansson, David's"
person.name.possessive(:abbreviated)  # => "D. Heinemeier Hansson's"


# Use directly
name = HasFullName::Name.full("David Heinemeier Hansson")
name.first # => "David"
```

## Installation

```ruby
# Gemfile
gem 'has_full_name'
```

If you are using this outside of Rails, make sure `ActiveRecord` and/or `ActiveModel` are manually required.

```ruby
require 'active_record'
# and/or
require 'active_model'
```

## License

Name of Person is released under the [MIT License](https://opensource.org/licenses/MIT).

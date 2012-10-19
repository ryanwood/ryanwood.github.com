---
layout: post
title: "Slither: A Dsl For Parsing Fixed Width Text Files"
date: 2009-06-12 12:54
comments: true
tags: [ruby dsl project]
---
Given the rage over XML and web services over the past decade or so, I was shocked at how common it is to still exchange data using a fixed-width file format over FTP. I guess it's all about those mainframes and backward compatibility, but "WOW".

At [work](http://firstdata.com) I have had numerous projects (mostly in Ruby) that involve creating and/or reading these fixed-width text files. Occasionally, I have the luxury of a CSV file and can use [FasterCSV](http://fastercsv.rubyforge.org/) to take care of business. To date, I haven't had a single project that used XML.

Given the need, I decided to create an open source project. I had to work on it primarily on my own time, as our work environment is not what you would call "open source friendly". So, [slither][1] was born.

## Definitions

Here's a simple example. Assume you have the following file format:

<style> 
  table#def { border-collapse: collapse; }
  table#def td { width: 100px; border: 1px solid #999; text-align: center;} 
</style>

<table id="def">
<tr><th>Position</th><th>Lenth</th><th>Field</th><th>Align</th></tr>
<tr><td>0</td><td>8</td><td>Date</td><td>-</td></tr>
<tr><td>8</td><td>4</td><td>Year</td><td>-</td></tr>
<tr><td>12</td><td>20</td><td>Make</td><td>left</td></tr>
<tr><td>32</td><td>20</td><td>Model</td><td>left</td></tr>
<tr><td>52</td><td>10</td><td>Name</td><td>left</td></tr>
<tr><td>62</td><td>6</td><td>Price</td><td>right</td></tr>
</table>

Here's a sample file (cars.txt).

    200606011999BMW                 325                Smith      45500
    200506011993Honda               Accord             Wood        7500
    200601022006Lexus               350                Johnson    25365

Given this file, we would first need to create a slither definition.

    Slither.define :cars do |d|
      d.section, :body do |body|
        # The trap is not very useful here since there is only one section
        body.trap { |line| line =~ /^\d{8}/ }
        body.column :date, 8
        body.column :year, 4
        body.column :make, 20, :align => :left
        body.column :model, 20, :align => :left
        body.column :name, 10, :align => :left
        body.column :price, 6
      end
    end

## Parsing

From there we could parse the above file like this:

    # Arguments are the file path and the definition name
    parsed_data = Slither.parse('cars.txt', :cars).inspect

It should return a hash with nested arrays keyed by section.

    result = {
      :body => [
        { :date => '20060601', 
          :year => '1999', 
          :make => 'BWW', 
          :model => '325', 
          :name => 'Smith', 
          :price => '45500' },
        ...
      ]
    }

## Generating

To generate a file, simply do the opposite. Create a properly formatted hash and call generate:

    # Generates the file as a string
    puts Slither.generate(:cars, my_car_hash)

    # Writes the file
    Slither.write('cars.txt', :cars, my_car_hash)

## Just the Beginning

There are many more things that Slither can do:

* headers and footers
* templated sections
* typecasting
* formatting
* validation (not quite there yet)

So go ahead and install the gem or [fork the Github project][1] if you're interested in hacking.

    # Run the following if you haven't already:
    gem sources -a http://gems.github.com
    # Install the gem(s):
    sudo gem install ryanwood-slither

[1]: http://github.com/ryanwood/slither/tree/master
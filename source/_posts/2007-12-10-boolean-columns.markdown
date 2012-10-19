---
layout: post
title: "Boolean Columns"
date: 2007-12-10 19:47
comments: true
tags: [rails tips]
---
Just found this little tidbit about [returning a boolean from a tinyint column](http://wiki.rubyonrails.org/rails/pages/HowtoUseBooleanColumns) tonight on the [rails wiki](http://wiki.rubyonrails.org/)...

Columns which are either boolean or tinyint(1) are recognised 
as booleans by ActiveRecord. So, if you have a table “people” and 
a column “rocks tinyint(1)”, you can say:

    person = People.find(1)
    person.rocks = true

However, person.rocks will return an integer, and Ruby thinks 
that 0 is true. If you want to test for truth, use person.rocks?, 
like this view example:

    message = "You rock, dude!" if person.rocks?

I did not know that. Pretty dang cool.
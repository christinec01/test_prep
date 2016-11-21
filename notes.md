1. Clone assessment Rails skeleton from GitHub

2. Find the seed file in /app/db and set up your models and migrations to reflect the data structure there

3. Write at least 5 model tests using RSpec

4. Write the controllers for your resources- you'll need to cover index and show for each reasource

5. Render an index and show page using ERB/HAML

6. Render a link that displays JSON data(this will go to another page that displays JSON, NOT an ajax call)
ie in the view you'll have two link_to's one that shows JSON, one that uses AJAX to append something to a page

in the show
```
@pack = Pack.find(prams[:id])

render :json => @pack.coyotes
end
```
or
```
def show
@pack = Pack.find(params[:id])
@coyotes = @pack.coyotes
respond_to do |f|
f.html { render json: @pack.coyotes }
end
end
```
7. Render a link that displays resource data via AJAX
in the index.html:
```
<% @pack.each do |pack|
<%= @pack.name %>
 <% = link_to,'show ajax', add remote:true, pack %>
 <% end %>
 ```
 
in the controller:
```
in show:
@pack = Pack.find(params[:id])
@coyotes = @pack.coyotes
responsd_to do |f|
f.js
end
```
make a partial coyotes/ _coyote with
```
<%=coyotes.howl %>(this can be whatever atttribute you've given a coyote in your migration)
```

in the show.js.erb:
target an empty div below the thing you want to append data to,
then append or prepend the data
```
$('div-name').preppend("<%= j (render @coyotes)'%>")
```

8. Import a CSS library to demonstrate asset pipeline knowledge
just use bootstrap in the asses pipeline


2 hours
<br>
they will give us a skeleton
<br>
we will need to fill in controllers and views and migrations and models (know how to generate migrations and models at the same time)
<br>
Know nested resources. From seed file you should be able to generate your models and migrations
To get rspec:
add the gem to the gemfile 
then do 'rails g rspec install' in the command line
then add the specs 
(look at rock, paper, scissors challenge) you wil be asked to validate attributes of a model 

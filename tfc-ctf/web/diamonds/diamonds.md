# Diamonds

### 385 points

## Information
    Author: skyv3il

    Write something nice that passes our filter.
 

## Steps done

1. We acceded to the URL Title "Ruby" content 
<img src="1.png" />
2. We sent a post with an "a" and the response was the same letter "a"
3. We tried submitting something like `<b>a</b>` and the response was
</br>
<img src="2.png" />
The site only allowed A-Z,a-z,0-9
4. We tried with a break line after the `a` and we sent `a
<%= IO.popen("ls /").readlines() %>` and we was able to did the directory listing
<img src="3.png" />
5. We navigate through the directories
<img src="4.png" />
6. And we read the flag file
<img src="5.png" />
TFCCTF{02718f35dddc266e0ac40c0c0dcc98c34edd545678dc752ba9831b6d73bc706f}


More info: We recovered the source from `/app/app/controllers``

```ruby
a require 'sinatra/base' 

class Animated_template < Sinatra::Base 
configure do 
    set :views, "app/views" 
    set :public_dir, "public" 
end 

get '/' 
do 
    @input = "Write something nice here that passes our regex " 
    erb :'index' 
end 

post '/' 
do 
    if params[:input] =~ /^[0-9a-z ]+$/i 
        @input = ERB.new(params[:input]).result(binding) 
    else 
        @input = "That is far away from nice !! " 
    end 
    erb :'index' 
end 

get '/style.css' 
do 
    erb :'style' 
end 
end
```




- References:
    - https://github.com/attackercan/regexp-security-cheatsheet
    - https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md#ruby---retrieve-etcpasswd



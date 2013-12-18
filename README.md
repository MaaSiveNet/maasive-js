#MaaSive.net JavaScript API

The MaaSive.net JavaScript API provides a convenient way for developers to access their MaaSive.net APIs.  Here are some examples:

##Setup

First include the library in your index.html file:

    <script src="js/maasive.js"></script>

Next, in your JavaScript file, initialize the object with the url of your API:
    
    maasive.host = 'https://api.maasive.net/v2/<your-api-id>'
    maasive.useEmRSVP = true;
    
Most of our examples use the [EmberJS framework](http://emberjs.com), so we are telling the library to use [RSVP](https://github.com/tildeio/rsvp.js/blob/master/README.md) Style Promises like Ember does.

##GET

To search a collection called *comments* for a document or set of documents, use the http GET method like this:

    var comments;
    comments = maasive.get('/comments/')
    
MaaSive returns a Promise, so you can chain 'thens' just like you would any other Promise like this:

    maasive.get('/comments/').then(function(data){alert('I got some comments');})
    
##POST

If you want to add some data to your comments collection, use POST like this:

    maasive.post('/comments/', data={text: 'I love MaaSive!'})
    
The library will handle setting up the XHR request for you and will stringify your data.

##Request

The standard REST methods are all syntactic sugar for the maasive.request() method.  If you prefer, you can use the request method directly like this:

    maasive.request({
        url: '/comments/123456',
        type: 'PUT',
        data: {text: 'MaaSive is super!'}
    })
    
The library will help you set up your request and serialize your data just like the other methods.
Node.js Freckle/Noko api bindings
=================================

Created by Tim Branyen [@tbranyen](http://twitter.com/tbranyen)

These bindings work specifically with the Noko (formally Freckle) V1 API.  If you are not currently using Noko for
time management, you totally should! It rocks! https://nokotime.com, it was created by @madrobby who
has been excellent with his support.

Note: Freckle was renamed to Noko in Q2/2019. Any references to Freckle or Noko are the same.

Installing
-----------------------

### Easy install (Recommended) ###
This will install and configure everything you need to use `freckle`.

    $ sudo npm install freckle

API Example Usage
-----------------

    var freckle = require( 'freckle' );

    // All freckle commands are sent over HTTPS

    // Add your own subdomain and API token information
    freckle( "mysubdomain", "askdfljsdjflkj3" );

    // List all users
    freckle.users.list(function( err, users ) {
      if( err ) {
        throw new Error( err );
      }

      console.log( users );
    });

    // Show a specific user
    freckle.users.show( 5, function( err, user ) {
      if( err ) {
        throw new Error( err );
      }

      console.log( user );
    });

    // Fetch a users api token
    freckle.users.token({ auth: [ "myemail@address.com", "mypassword" ] }, function( err, token ) {
      if( err ) {
        throw new Error( err );
      }

      console.log( token );
    });

    // Adding a new time entry
    freckle.entries.add({
      'entry': {
        'minutes': "1hr"
      , 'user': "myemail@address.com"
      , 'project_id': 54
      , 'description': 'opensource'
      , 'date': freckle.date( new Date )
      }
    }, function( err, data ) {
      if( err ) {
        throw new Error( err );
      }

      console.log( err, data );
    });


####Search Example Usage

see http://madrobby.github.io/freckle-apidocs/entries.html for search argument specification.

    // List all PROGRAMMING entries
    var args = {'search': {'tags': 'PROGRAMMING'}};
    freckle.entries.search(args, function( err, entries ) {
      if( err ) {
        throw new Error( err );
      }

      console.log( entries );
    });

Note: When dealing with the entries API, use the `search` command instead of the `list` command. All pages of entries will be returned at once so the result set can become quite large if you do not use search with proper filters.


Release information
-------------------

### v0.0.2: ###
    * Rename to noko

### v0.0.1: ###
    * Initial potentially complete bindings

Getting involved
----------------

If you find this project of interest, please document all issues and fork if you feel you can provide a patch.

---
layout: default
title: API -- Trust Exchange, NodeMap, Diff, Merge
---


Enlightened Structure APIs
==========================

RESTful API, defined as Rails-style routes:

NodeMap
-------

    post '/' => 'nodes#create'    # POST params: { :content => content_blob }   # returns key
    get  '/:key' => 'nodes#show', :constraints => { :key => SHA512_PATTERN }
    get '/' => 'nodes#index'

NodeSentences
-------------

    post '/' => 'nodes#create'    
        #  format: json|xml|yaml
        #  POST params: 
        #    { :node => arbitrary_data_structure }
        #    
        #  eg: 
        #    { :content => 
        #       "{
        #           subject: '262a544a03fe39e55a5d60353affc9c421501362d9a16b2d32d152d2a40976deee1bd0786a5ce40513e064d45cb8fbd42b3ca9b7bb8c849f7a38a95a8f85415a'
        #           predicate: 'feeaceca3e72f3dec300bc28857374344508ec64f7fd54e5f90d13312c5fdc14acf8c5fd406d49ad6bf24d5a74132a61406f3574f583c5e7961e597da12e89b9'
        #           subject: '6b7697db17971492fcc75774d3df34954ccf4037e603e2820e8542467304fc8221cf47593d1eb87e29cfd88332966e35ac49bc2b7f848a71683a22da251bc442'
        #        }"
        #    }
        
    get  '/:key' => 'nodes#show', :constraints => { :key => SHA512_PATTERN } 
    get '/' => 'nodes#index'

Diff
----

    get '/nodes/compare/:before..:after', 'nodes#compare_blobs',
      :constraints => { :before => /#{SHA512_PATTERN}/, :after => /#{SHA512_PATTERN}/ }

    get '/nodes/compare/:before_url..:after_url', 'nodes#compare_from_urls'

Merge
-----
    
    post '/nodes/:id/merge' => 'nodes#merge', :constraints => { :id => /#{SHA512_PATTERN}/ }
        # POST params: { :patch => patch_text }

    get '/nodes/:id/merge/:patch' => 'nodes#merge', :constraints => { :id => /#{SHA512_PATTERN}/, :patch => /#{SHA512_PATTERN}/ }

    # todo: merge conflict resolution API
    
Trust Exchange
--------------

    post '/' => 'ratings#create'  
        # POST params: 
        # { 
        #    :entity => entity_name,            # eg google.com
        #    :category => category_name,        # eg integrity
        #    :rating => [0..1]                  # eg 0.77
        #    :public_key => users_public_key    # eg 'GiBDv2vMARBACPHw...'
        # } 

    get  '/:key' => 'ratings#show', :constraints => { :key => SHA512_PATTERN }

    # show recent ratings of interest
    get '/' => 'ratings#index'
    
    # show ratings of an entity
    get '/entities/:entity' => 'ratings#index'
    
    # show ratings of an entity by a given user
    get '/users/:user/entities/:entity' => 'ratings#index'

    # show ratings of an entity by a given user within a category
    get '/users/:user/entities/:entity/categories/:category' => 'ratings#index'
    
    # show ratings by a given user within a category
    get '/users/:user/categories/:category' => 'ratings#index'

    # show ratings of an entity within a category
    get '/entities/:entity/categories/:category' => 'ratings#index'    


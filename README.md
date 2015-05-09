redis puppet module
===================

*I am a fork. I give thanks to thomasvandoren, whose code I forked. Ideally, I'd like development to continue in the upstream repository, but I'm unsure of the status of  development, and note that some pull requests haven't been answered for around 10 months (including mine, to add Redis 3 Cluster support, and rework the configs for better cross-version compatibility). Thus, for the time being, I have merged my code into master, and am accepting pull requests. I intend to contact upstream again, and offer assistance. [tiredpixel]*

[![Build Status](https://secure.travis-ci.org/thomasvandoren/puppet-redis.png)](http://travis-ci.org/thomasvandoren/puppet-redis)

Install and configure redis.

Usage
-----
Installs redis server and client with reasonable defaults.

```puppet
include redis
```

Installs redis server and client with version 2.6.5.

```puppet
class { 'redis':
  version => '2.6.5',
}
```

Installs version 2.6.17, listens on default port 6379 with default settings.
Sets up 2nd instance on port 6900, binds to address 10.1.2.3 (instead of all 
available interfaces), sets max memory to 1 gigabyte, and sets a password from 
hiera.

```puppet
class { 'redis':
  version            => '2.6.17',
}
redis::instance { 'redis-6900':
  redis_port         => '6900',
  redis_bind_address => '10.1.2.3',
  redis_password     => hiera('redis_password'),
  redis_max_memory   => '1gb',
}
```

Development
-----------

To run the linter and spec tests locally:

```bash
bundle install --gemfile .gemfile
rake lint
rake spec
```

Authors
-------
Thomas Van Doren

License
-------
BSD

# My home assistant config

I run home assistant inside a local kubernetes cluster on my home network.  I'm not aware of any
well-supported helm charts for doing this, so I'm rolling my own that works well specifically for my
purposes.

It's just a start, and it's probably not useful to anyone else right now unless you want to see how
I implement any of the following.  If you think there's something interesting in here that you'd be
interesting _if only I'd change it somehow_, feel free to reach out.  I'd love to see this
eventually be useful to others, too.


### Direct Plugin Support

There are some plugins that I'm interested in using with home assistant that aren't official, and so
historically I kept a local volume holding those plugins in my cluster, available for home
assistant, but difficult to see unless you hopped into the pod.  Certainly there was no useful way
of testing them prior to running.  Nor was there an easy way of keeping them up to date.

My plan is to incorporate these at build time rather than at runtime.  I should be able to create a
build pipeline that pulls down new versions of those when available, potentially runs some tests,
and then I expect to see a new version turn up on my cluster.

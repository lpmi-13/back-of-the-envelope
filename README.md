# Back of the envelope

This is a simple web app to practice doing the sorts of calculations that you might come across in a simple system design task.

For example, estimating the traffic for an image sharing service:

> If you have 10,000 users and each of them upload an average of 10 photos per day, that's 100,000 requests to your upload photo endpoint per day, translating to roughly 1 request per second (100,000 / (24 * 60 * 60) = 1.16)

Or for estimating total storage needs:

> If each photo is about 250KB, and you'd like to store all photos (even soft deletes) for 5 years, then you need 100,000 * 250KB * 365 * 5...which comes out to about 45.6 TB

Or for estimating badwidth needs for the network:

> If each photo is 250KB, on average, and we see about 1 request per second, then we need to handle 250KB/sec incoming data

Or for estimating distribution of reads/writes:

> If we expect roughly 5/1 ratio of reads (users viewing photos) to writes (users uploading photos), then we should expect to handle 5 requests per second, and 1.25MB/sec of outgoing data, in terms of bandwidth

Or even for what sort of caching we would need:

> If we expect roughly 20% of the photos will be 80% of the viewing requests, we could put them into a caching layer. So we would need to deal with 500,000 total read requests per day, estimating that 20% of them (100,000) would be efficient to cache, then we need to allocate 100,000 * 250KB of cache space (25GB).

...None of these examples necessarily take into account scaling for expected growth in the service, but they're broadly the categories of things that are helpful to estimate during initial planning of a new system.

## Local development

```
npm start
```
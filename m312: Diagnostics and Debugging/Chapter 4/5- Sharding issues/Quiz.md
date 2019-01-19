**Chapter 4: Connectivity**

## Sharding Issues

**Problem**

Assuming the default chunk size, which of the following is/are jumbo chunks?

Check all answers that apply:

- [ ] 10 MB
- [ ] 20 MB
- [ ] 50 MB
- [ ] 100 MB
- [ ] 200 MB
- [ ] 500 MB
___
**Answer**

The default chunk size is 64 MB. 50 MB is below this, so all choices below and including 50 MB were wrong. The answers 100 MB and above are correct. You could see in the video that the balancer wouldn't move these until we changed the chunk size.

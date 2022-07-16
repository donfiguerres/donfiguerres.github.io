---
title: "Java Performance Testing Using Zerocode"
description: "Java Performance Testing Using Zerocode"
date: 2022-06-22T23:10:00+08:00
hero: images/zerocode-banner.png
menu:
  sidebar:
    name: "Java Performance Testing Using Zerocode"
    identifier: java-performance-testing-using-zerocode
    parent: java
---

In one of my previous projects, I had to add a performance testing suite for
our Java APIs to measure the performance gain in the performance improvement
that I was working on.

After some research, I found that [Zerocode](https://zerocode.io/) is able to
fulfill our needs. Their [GitHub Repo](https://github.com/authorjapps/zerocode)
also includes an extensive documentation which made the process much easier for
me.

I found that you can reuse your existing JUnit tests as performance tests using
the LoadWith annotation.

For example, I have a unit test below. Take note that I have also used the
`RunWith` annotation to use the `ZeroCodeUnitRunner` class.

```java
@RunWith(ZeroCodeUnitRunner.class)
public class MyUnitTest {
    @Test
    public void testDefaultPass() {
        Assert.assertTrue(true);
    }
}
```

Then, I can reuse this test as a performance test like in the example below.

```java
@LoadWith("load_config.properties")
@TestMapping(testClass = MyUnitTest.class, testMethod = "testDefaultPass")
@RunWith(ZeroCodeLoadRunner.class)
public class LoadTest {
}
```

Take note that the class itself is empty. The load test is defined with the
`LoadWith` and `TestMapping` annotations. The `LoadWith` annotation is used
to specify the properties file where you can configure your load tests. In the
example below, the threads, ramp-up period, loop count and abort time-out are
defined in the properties file.

```properties
number.of.threads=2
ramp.up.period.in.seconds=10
loop.count=1
abort.after.time.lapsed.in.seconds=600
```

A more complete documentation is found [here](https://github.com/authorjapps/zerocode/wiki/Load-or-Performance-Testing-(IDE-based)).

I also found this [blog from Baeldung](https://www.baeldung.com/zerocode-intro)
to be helpful when I was working on adding zerocode performance test.

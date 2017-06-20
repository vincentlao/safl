# Safl
**S**tand-**a**lone **F**uture **L**ibrary is a C++ library which provides builing
blocks for developing an asynchronous software using the Future/Promise pattern.

## Background
A concept behind the library is inspired by <a href="https://github.com/facebook/folly
/tree/master/folly/futures">Folly Futures</a>. But, in contrast to it, _safl_ is
not a part of any framework and thus depends only on the C++ standard library.

Besides that, there are several differences in a design of the library. First of
all, C++ exceptions are completely banned. Therefore, error handling is not based
on exceptions and a client code must not throw.

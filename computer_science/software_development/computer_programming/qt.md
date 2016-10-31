#[Qt](https://www.qt.io/)
Cross-platform software development for embedded & desktop 

##PIMPL [How to use the Qt's PIMPL idiom?](http://stackoverflow.com/questions/25250171/how-to-use-the-qts-pimpl-idiom)

a minimal pimpl-based interface, not derived from QObject
```
// Foo.h
#include <QScopedPointer>
class FooPrivate; ///< The PIMPL class for Foo
class Foo {
  QScopedPointer<FooPrivate> const d_ptr;
public:
  Foo();
  ~Foo();
};

// Foo.cpp
class FooPrivate { };
Foo::Foo() : d_ptr(new FooPrivate) {}
Foo::~Foo() {}
```


QObject's PIMPL
```
class FooPrivate;
class Foo : public QObject {
  Q_OBJECT
public:
  ...
private:
  Q_DECLARE_PRIVATE(Foo);
  QScopedPointer<FooPrivate> const d_ptr;
};

// Foo.cpp
class FooPrivate
{
public:
  ...
private:
  Q_DISABLE_COPY(FooPrivate);
  Q_DECLARE_PUBLIC(Foo);
  FooPrivate(Foo* ptr);
  Foo* q_ptr;
};

FooPrivate::FooPrivate(Foo* ptr)
  : q_ptr(ptr) {}

Foo::Foo()
  : d_ptr(new FooPrivate(this)) {}

Foo::~Foo() {}

#include "foo.moc"
```

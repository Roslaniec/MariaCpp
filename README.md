<!-- -*- mode: markdown -*-  -->

MariaCpp is C++ library that lets you connect to the MariaDB Server
(or MySQL Server).


Major features of MariaCpp
--------------------------

*   __LGPL__ license

*   thin C++ wrapper around _MariaDB Connector/C_ (C-API);
    _thin_ means that C++ objects have none (or minimal) internal state,
    and you can possibly mix C++ code with native C-API

*   works with C++98, C++11, C++14 standards

*   it takes benefits of 2 major C++ paradigms: __RAII__ and __exceptions__

*   supports most C-API features, including __prepared statements__

*   supports __multithreading__ (multiple connections to DB)



FAQ
===

**Q**: There exists already MySQL Connector/C++. What's the benefit of MariaCpp?

**A**: The primary difference is a license: MySQL Connector/C++ is __GPL__.
   MariaCpp is licensed as LGPL (__Lesser GPL__).
   Other difference is that _MySQL Connector/C++_ is based on JDBC 4.0 API,
   while MariaCpp API is based on  _MariaDB Connector/C_.
   Nevertheless, migration from MySQL Connector/C++ might be surprisingly easy.

* * *

**Q**: Can I use _MariaCpp_ with _MySQL Connector/C_ as underlying library
   instead of _MariaDB Connector/C_?

**A**: Yes, you can. But please notice that _MySQL Connector/C_ is GPL licensed.
   As result, your code must be GPL licensed as well (or other FLOSS license).
   Sometimes it's not desirable.

* * *

**Q**: Why _MariaCpp_ is licensed as LGPL?

**A**: MariaCpp is licensed in the same spirit as _MariaDB Connector/C_.

* * *


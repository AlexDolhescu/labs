#Limbajul Python

---

#Obiective

- Prezentarea limbajului Python
- Pregătirea mediului de lucru
- Familiarizarea cu limbajul
    - Tipuri de date (int, float, *long*, str)
    - Operatori
    - Comentarii
    - Funcții built-in (print, input, *raw_input*, open)
    - Instrucțiuni condiționale (if - elif - else)
 
*Timp estimat: **45** de minute*

---

#Limbajul Python

---

#Implementări ale limbajului

- **CPython - [python.org](https://www.python.org/)**
- Jython - [jython.org](http://www.jython.org/)
- Python for .NET - [pythonnet.sourceforge.net](http://pythonnet.sourceforge.net/)
- IronPython - [ironpython.net](http://ironpython.net/)
- PyPy - [pypy.org](http://pypy.org/)

---

#Instalarea

Mai multe detalii pe link-urile de mai jos:

- **CPython** - [python.org/downloads/](https://www.python.org/downloads/)
- Jython - [jython.org/downloads.html](http://www.jython.org/downloads.html)
- Python for .NET - [http://sourceforge.net/projects/pythonnet/files/](http://sourceforge.net/projects/pythonnet/files/)
- IronPython - [ironpython.net/download/](http://ironpython.net/download/)
- PyPy - [pypy.org/download.html](http://pypy.org/download.html)


---

#Interpretorul

```
~ $ python3
```

    !python
    Python 3.4.0 (default, Jun 19 2015, 14:20:21) 
    [GCC 4.8.2] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> dir
    <built-in function dir>
    >>> help
    Type help() for interactive help, or help(object) for help about object.
    >>> help(dir)

    >>> 

Funcții foarte utile:  ```dir(...)``` și ```help(...)```.

---

#Interpretorul

```
~ $ python3 search.py "Python România"
```
    
    !text
    Titlu: <b>Python</b> Weekend @Iași - RoPython
        URL:https://conference.ropython.org/
    Titlu: LocalUserGroups - <b>Python</b> Wiki
        URL:https://wiki.python.org/moin/LocalUserGroups
    Titlu: <b>Romania</b> | <b>Python</b> Data Recovery
        URL:http://www.python.ro/romania
    Titlu: <b>Python</b> Data Recovery | Recover every bit
        URL:http://www.python.ro/


```
~ $ cat search.py
```

    !python
    import sys
    import requests

    def search(query):
        url = "http://ajax.googleapis.com/ajax/services/search/web"
        params = {"v": "1.0", "q": query}
        response = requests.get(url, params=params)
        data = response.json()
        for result in data["responseData"]["results"]:
            print("Titlu: {}\n\tURL:{}".format(result["title"],
                                               result["url"]))

    if __name__ == "__main__":
        search(sys.argv[1])

---

#Mediul de lucru

- Editor text:
    - Sublime Text
    - Notepad++
    - Vim

Mai multe exemple aici: [en.wikipedia.org/wiki/List_of_text_editors](https://en.wikipedia.org/wiki/List_of_text_editors).

- IDE-uri pentru Python:
    - Komodo (Windows/Linux/Mac OS X)
    - LiClipse (Linux/Mac OS X/Windows)
    - PyCharm (Linux/Mac OS X/Windows)
    - Wing IDE (Windows, Linux, Mac OS X)

Mai multe exemple aici: [wiki.python.org/moin/IntegratedDevelopmentEnvironments](https://wiki.python.org/moin/IntegratedDevelopmentEnvironments).

---

#Operatori

---

#Operatori booleeni

    !python
    >>> True or False
    True
    
    >>> True and False
    False
    
    >>> not True
    False
    
    >>> not False
    True

---

#Operatori pentru comparație

    !python
    >>> x < y
    False
    
    >>> x <= y
    True
    
    >>> x > y
    False
    
    >>> x >= y
    True
    
    >>> x == y
    True
    
    >>> x != y
    False
    
    >>> x is y
    True
    
    >>> x is not y
    False

---

#Operatori pentru operații matematice

    !python
    >>> 4 + 5
    9
    
    >>> 4 - 5
    -1
    
    >>> 5 / 2
    2
    
    >>> 5 // 2
    2
    
    >>> 5 % 2
    1
    
    >>> -5
    -5
    
    >>> +5
    5

În Python 3.x

    !python
    >>> 5 / 2
    2.5
    >>> 5 // 2
    2

---

#Operatori binari

    !python
    >>> 2 | 4
    6
    
    >>> 2 ^ 4
    6
    
    >>> 2 & 4
    0
    
    >>> 1 << 3
    8
    
    >>> 8 >> 3
    1
    
    >>> ~8
    -9

---

#Tipuri de date

---

#Tipuri de date numerice

**Intreg**
    
    !python
    >>> 10
    10
    >>> int(100)
    100
    
    >>> dir(int(10))
    ['...', 'bit_length', 'conjugate', 'denominator', 'imag',
     'numerator', 'real']
    
    >>> int(10).bit_length()
    4
    
    >>> int(10).conjugate()
    10
    
    >>> int(10).denominator
    1
    
    >>> int(10).numerator
    10

---

#Tipuri de date numerice

**Float**
    
    !python
    >>> 10.0
    10.0
    >>> float(10)
    10.0
    
    >>> dir(float(10))
    ['...', 'as_integer_ratio', 'conjugate', 'fromhex', 'hex', 'imag',
     'is_integer', 'real']
    
    >>> float(10).as_integer_ratio()
    (10, 1)
    
    >>> float(10).hex()
    '0x1.4000000000000p+3'
    
    >>> float(10).is_integer()
    True

---

#Tipuri de date numerice

**Long - Python 2.x**
    
    !python
    >>> sys.maxint + 1
    9223372036854775808L
    >>> type(_)
    <type 'long'>
    >>> long(10)
    10L
    
    >>> dir(long(10))
    ['...', 'bit_length', 'conjugate', 'denominator', 'imag',
     'numerator', 'real']
    
    >>> (sys.maxint + 1).denominator
    1L
    
    >>> (sys.maxint + 1).imag
    0L
    
    >>> (sys.maxint + 1).real
    9223372036854775808L
    
    >>> (sys.maxint + 1).conjugate()
    9223372036854775808L
    >>> (sys.maxint + 1).bit_length()
    64

---

#Tipuri de date numerice

**Complex**
    
    !python
    >>> a = complex(10, 5)
    >>> a
    (10+5j)
    
    >>> dir(a)
    ['...', 'conjugate', 'imag', 'real']
    
    >>> a.imag
    5.0

    >>> a.real
    10.0

    >>> a.conjugate()
    (10-5j)

---

#Tipuri de date booleene
    
    !python
    >>> True
    True
    >>> False
    False
    >>> bool(1)
    True
    >>> bool(0)
    False

    >>> dir(bool(1))
    ['...', 'bit_length', 'conjugate', 'denominator', 'imag',
     'numerator', 'real']
    >>> bool(1).bit_length()
    1

---

#Șirurile de caractere
    
    !python
    sir1 = 'Acesta este un sir de caractere'
    sir2 = "Acesta este un sir de caractere"
    sir3 = """Acesta este un sir de caractere
    pe mai multe linii."""
    sir4 = '''Acesta este un sir de caractere
    pe mai multe linii.'''
    sir5 = (
        "Acesta este un sir de caractere foarte"
        " lung, dar care totusi este pe o singura "
        " linie."
    )
    
    >>> dir("")
    ['...', 'capitalize', 'center', 'count', 'decode', 'encode',
     'endswith', 'expandtabs', 'find', 'format', 'index', 'isalnum',
     'isalpha', 'isdigit', 'islower', 'isspace', 'istitle', 'isupper',
     'join', 'ljust', 'lower', 'lstrip', 'partition', 'replace', 'rfind',
     'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split',
     'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate',
     'upper', 'zfill']

---

#Șirurile de caractere

    !python
    >>> "Ana are mere.".capitalize()
    'Ana are mere.'

    >>> "ana are mere.".center(62)
    '                        ana are mere.                         '
    >>> "ana are mere.".count("a")
    3

    >>> "ana are mere.".endswith("mere.")
    True

    >>> "ana are mere.".startswith("ana")
    True

    >>> "ana are mere.".partition("are")
    ('ana ', 'are', ' mere.')
    
    >>> "ana are mere.".upper()
    'ANA ARE MERE.'
    
    >>> "ana are mere.".title()
    'Ana Are Mere.'
    
    >>> "ana are mere.".split()
    ['ana', 'are', 'mere.']

---

#Șirurile de caractere

    !python
    >>> "%s are mere." % "Ana"
    'Ana are mere.'

    >>> "%s are %s." % ("Ana", "mere")
    'Ana are mere.'

    >>> "%(nume)s are %(fructe)s." % {"nume": "Ana", "fructe": "mere"}
    'Ana are mere.'

    >>> "{} are {}.".format("Ana", "mere")
    'Ana are mere.'

    >>> "{nume} are {fructe}.".format(nume="Ana", fructe="mere")
    'Ana are mere.'

---

#Comentarii
    
    !python
    """
    Acesta este un comentariu.
    """

    # Acesta este un comentariu


---

#Funcții built-in

---

#Funcții built-in

**print** - Scrie un mesaj într-un stream (predefinit este stdout)

```
print(value, ..., sep=' ', end='\n', file=sys.stdout)
```

    !python
    >>>from __future__ import print_function

    >>> print("ana", "are", "mere")
    ana are mere
    
    >>> print("Ana", "are", "mere", end='\n')
    Ana are mere
    
    >>> print("Ana", "are", "mere", sep='\n')
    Ana
    are
    mere

---

#Funcții built-in

**input** și **raw_input** - citesc informații de la tastatură

    !python
    >>> raw_input("Ana are: ")
    Ana are: mere
    'mere'
    
    >>> input("Numarul de mere pe care le are ana este: ")
    Numarul de mere pe care le are ana este: 10
    10
    
    >>> type(_)
    <type 'int'>
    
    >>> raw_input("Numarul de mere pe care le are ana este: ")
    Numarul de mere pe care le are ana este: 10
    '10'
    
    >>> type(_)
    <type 'str'>

*raw_input* este prezent doar în Python 2.x

---

#Funcții built-in

**open** deschide un fișier

```
open(name[, mode[, buffering]])
```

    !python
    >>> file_handle = open("test.tuxy", "w")
    >>> file_handle.write("Tuxy Pinguinescu este cel mai tare.")
    >>> file_handle.close()

    >>> file_handle = open("test.tuxy", "r")
    >>> file_handle.read()
    'Tuxy Pinguinescu este cel mai tare.'
    >>> file_handle.close()

---

#Funcții built-in

    !python
    >>> dir(__builtins__)
    
    ['...'. 'abs', 'all', 'any', 'apply', 'basestring', 'bin', 'bool',
     'buffer', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod',
     'cmp', 'coerce', 'compile', 'complex', 'copyright', 'credits',
     'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'execfile',
     'exit', 'file', 'filter', 'float', 'format', 'frozenset', 'getattr',
     'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int',
     'intern', 'isinstance', 'issubclass', 'iter', 'len', 'license',
     'list', 'locals', 'long', 'map', 'max', 'memoryview', 'min',
     'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property',
     'quit', 'range', 'raw_input', 'reduce', 'reload', 'repr', 'reversed',
     'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str',
     'sum', 'super', 'tuple', 'type', 'unichr', 'unicode', 'vars', 'xrange',
     'zip'
    ]

---

#Instrucțiuni condiționale

---

# if - elif - else
    
    !python
    if_stmt ::=  "if" expression ":" suite
                 ( "elif" expression ":" suite )*
                 ["else" ":" suite]

-

    !python
    >>> if numar % 5 == 0 and numar % 3 == 0: 
    ...     pass
    ... elif numar % 7 == 0:
    ...     pass
    ... else:
    ...     pass
    ... 

---

#Exerciții

    !python
    #!/usr/bin/env python
    # *-* coding: UTF-8 *-*
    """Scrieți o funcție ce să determine dacă numărul primit
    ca argument este par.
    
    Cerințe:
        - Se va folosi structura condițională if-elif-else
    """
    
    
    def par(numar):
        """Funcție ce determină dacă un număr este par."""
        pass
        
    if __name__ == "__main__":
        assert not par(1)
        assert par(2)
        assert not par(3)

---

#Exerciții

    !python
    #!/usr/bin/env python
    # *-* coding: UTF-8 *-*
    """Scrieți o funcție ce să determine maximul dintre două
    numere primite ca argument.
    
    Cerințe:
        - Se va folosi structura condițională if-elif-else
        - Nu se va folosi funcția max
    """
    
    
    def maxim(numar1, numar2):
        """Funcție ce determină maximul dintre două numere."""
        pass
    
    if __name__ == "__main__":
        assert maxim(1, 2) == 2
        assert maxim(5, 6) == 6
        assert maxim(1, 1) == 1

---

#Exerciții

    !python
    #!/usr/bin/env python
    # *-* coding: UTF-8 *-*
    """Scrieți o funcție ce să determine dacă numărul primit
    ca argument este o putere a lui 2.
    """
    
    
    def putere(numar):
        """Funcție ce determină dacă un număr este putere a lui 2."""
        pass
    
    if __name__ == "__main__":
        assert putere(2)
        assert putere(4)
        assert not putere(10)

---

#Exerciții

    !python
    #!/usr/bin/env python
    # *-* coding: UTF-8 *-*
    """Scrieți o funcție ce să determine dacă șirul de caractere
    primit ca argument este palindrom.
    """
    
    
    def palindrom(sir):
        """Funcție ce determină dacă șirul primit este palindrom."""
        pass
    
    if __name__ == "__main__":
        assert not palindrom("python")
        assert palindrom("radar")
        assert not palindrom("palindrom")

---

#Resurse

- www.python.org
- www.learnpython.org/
- www.learnpythonthehardway.org
- www.corepython.com
- www.codecademy.com/tracks/python
- www.checkio.org
- www.ropython.org
- www.github.com/RoPython
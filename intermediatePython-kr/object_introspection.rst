Object introspection
--------------------

(컴퓨터 프로그래밍에서 실행시 object의 타입을 알아내는 것은 중요합니다?)
이것은 python의 강점 중 하나입니다. python에서는 모든것이 하나의 object이며
그것을 조사할 수 있습니다. Python은 우리를 도와줄 몇가지 함수와 모듈을 포함
하고 있습니다.

``dir``
^^^^^^^^^^^

이곳에서는 ``dir`` 에 대해 알아 볼 것이며 우리가 이것을 어떻게 알아 낼 수
있는지에 대해  알아 볼 것입니다. 

이것은 속성을 알아보는 것중에 가장 중요한 함수입나다. 이것은 소유하고 있는
메소드들과 속성들을 리스트로 반환해 줍니다. 
여기 예제 입니다.:

.. code:: python

    my_list = [1, 2, 3]
    dir(my_list)
    # Output: ['__add__', '__class__', '__contains__', '__delattr__', '__delitem__',
    # '__delslice__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__',
    # '__getitem__', '__getslice__', '__gt__', '__hash__', '__iadd__', '__imul__',
    # '__init__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__',
    # '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__',
    # '__setattr__', '__setitem__', '__setslice__', '__sizeof__', '__str__',
    # '__subclasshook__', 'append', 'count', 'extend', 'index', 'insert', 'pop',
    # 'remove', 'reverse', 'sort']

우리에게 list의 methods 이름들을 알려줍니다. 이것은 여러분이 메소드 이름을
떠오르게 하여 다룰수 있게 합니다. ``dir()`` 을 어떠한 인자도 없이 실행 시킨다면
현재 상태의 모든 이름을 return해 줄 것입니다.

``type`` 과 ``id``
^^^^^^^^^^^^^^^^^^^^

``type`` 함수는 object의 타입을 반환해 줍니다.
다음 예제를 보세요.:

.. code:: python

    print(type(''))
    # Output: <type 'str'>

    print(type([]))
    # Output: <type 'list'>

    print(type({}))
    # Output: <type 'dict'>

    print(type(dict))
    # Output: <type 'type'>

    print(type(3))
    # Output: <type 'int'>

``id`` 는 다양한 object의 유니크한 id를 반환해줍니다. 
다음 예제를 보세요.

.. code:: python

    name = "Yasoob"
    print(id(name))
    # Output: 139972439030304

``inspect`` module
^^^^^^^^^^^^^^^^^^^^^^
inspect module 또한 살아있는 object들에 대한 유용한 정보를 주는 함수를 포함
하고 있습니다. 예를 들어 실행중인 object의 멤버를 체크하고 싶다면 다음과 같이
알아 볼 수 있습니다.:

.. code:: python

    import inspect
    print(inspect.getmembers(str))
    # Output: [('__add__', <slot wrapper '__add__' of ... ...

(여러 method들에게 도움이 될만한 정보를 줍니다.?)
원한다면 좀 더 알아 본다면 좋을 거 같습니다.

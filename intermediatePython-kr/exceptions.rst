Exceptions
----------

Exception handling is an art which once you master grants you immense
powers. I am going to show you some of the ways in which we can handle
exceptions.
예외 처리는 어마어마하게 중요합니다? 예외를 처리하는 방법 몇가지를
보여드리겠습니다.


가장 기본적인 ``try/except`` 구문을 알아 보겠습니다.
예외가 일어 날 수있는 코드를 ``try`` 블록에 넣고 발생한 예외를 처리할 코드를
``except`` 블록에 넣으면 됩니다. 
간단한 예제를 봅시다. :

.. code:: python

    try:
        file = open('test.txt', 'rb')
    except IOError as e:
        print('An IOError occurred. {}'.format(e.args[-1]))

위의 예제는 IOError 예외에 대해서만 처리합니다. 초보자일땐 여러가지 예외를 처리
할 수있다는 것을 알지 못할 수도 있습니다.

여러가지 예외처리:
^^^^^^^^^^^^^^^^^^
우리는 세가지 방법으로 여러 예외를 처리할 수 있습니다. 
첫번째 방법으로는 일어날수 있는 예외들을 튜플로 넣는 것이죠.
다음과 같이 말입니다. :

.. code:: python

    try:
        file = open('test.txt', 'rb')
    except (IOError, EOFError) as e:
        print("An error occurred. {}".format(e.args[-1]))

다른 방법으로는 ``except`` 블럭을 예외별로 나누는 것이죠. 
우리는 원하는 만큼 ``except`` 블럭을 만들 수 있습니다.
다음 예제를 보세요. :

.. code:: python

    try:
        file = open('test.txt', 'rb')
    except EOFError as e:
        print("An EOF error occurred.")
        raise e
    except IOError as e:
        print("An error occurred.")
        raise e

(마지막 방법은 첫번째와 같이 특정 예외가 아닌 모든 예외를 한번에 처리하는
방법입니다. 한번 보시죠. :)

.. code:: python

    try:
        file = open('test.txt', 'rb')
    except Exception:
        # Some logging if you want
        raise

(이 방법은 당신의 프로그램이 던진 예외에 대해 별다른 아이디어가 없을때 유용합니다. )
``finally`` 구문
~~~~~~~~~~~~~~~~

우리는 메인코드를 ``try`` 구문 안에 넣었습니다.
그다음 ``except`` 구문에 ``try`` 구문에서 발생되는 예외에 대해서 실행할 코드를 
넣어두었지요.

이번 예제에서는 ``finally`` 라는 구문을 사용 할 것입니다.
``finally`` 블럭에 있는 코드는 예외가 발생하던 발생하지 않던 실행되는
구문입니다.
(스크립트를 작동하기 전 깨끗하게 하기 위함입니다.) 다음 간단한 예제를 보시죠. :

.. code:: python

    try:
        file = open('test.txt', 'rb')
    except IOError as e:
        print('An IOError occurred. {}'.format(e.args[-1]))
    finally:
        print("This would be printed whether or not an exception occurred!")
        
    # Output: An IOError occurred. No such file or directory
    # This would be printed whether or not an exception occurred!

``try/else`` 구문
~~~~~~~~~~~~~~~~~

때때로는 코드가 예외를 일으키지 않았을때 작동시키고 싶은 코드가 있을 수
있습니다.
이럴때는 ``else`` 구문을 이용하여 쉽게 처리할 수 있습니다.
어떤 사람은 이렇게 말할 수 있습니다. 
    예외를 발생시키지 않았을때 작동 하고 싶으면 간단하게 
    코드를 ``try`` 블럭 안에 넣으면 되지 않아?
    
(``try`` 구문에 있는 코드가 예외를 발생시킨다면 다 잡아내는것을 원하지 않기
때문입니다.) 라고 답할 수 있을 것입니다.
솔직히 많은 사람들이 사용하진 않습니다. 물론 저를 포함해서 말이죠.
다음 예제가 있습니다.

.. code:: python

    try:
        print('I am sure no exception is going to occur!')
    except Exception:
        print('exception')
    else:
        # any code that should only run if no exception occurs in the try,
        # but for which exceptions should NOT be caught
        print('This would only run if no exception occurs. And an error here '
              'would NOT be caught.')
    finally:
        print('This would be printed in every case.')

    # Output: I am sure no exception is going to occur!
    # This would only run if no exception occurs.
    # This would be printed in every case.

``else`` 구문에 있는 코드는 예외가 발생하지 않는다면 ``finally`` 구문 전에
실행이 될 것입니다.

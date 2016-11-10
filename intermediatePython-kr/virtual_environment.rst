Virtual Environment
-------------------

``virtualenv`` 라고 들어 보셨나요? ``virtualenv`` 에 대해 들어보지 못했을 수도
있어요. toolset으로 편하게 사용중일 수도 있습니다.
그래서 ``virtualenv`` 가 뭐냐구요?
``Virtualenv`` 는 다양한 파이썬 환경을 사용 할 수 있게 도와주는 도구입니다.
어떤 어플리케이션이 어떤 라이브러리의 2버전을 필요로 합니다. 다른 어플리
케이션은 그 라이브러리의 3버전이 필요하다고 생각해보세요. 어떤 방식으로 두가지
어플리케이션을 사용하며 개발을 할 것인가요?

``/usr/lib/python2.7/site-packages`` 에 모두 설치했다면, 
그 솔루션은 의도치 않게 패키지가 업그레이드 되고 말 것입니다.

In another case, imagine that you have an application which is fully
다른 경우는 개발을 끝낸 어플리케이션을 갖고 있으며 그
어플리케이션에 관련된 어떠한 라이브러리도 변경을 원하지 않는 다고 생각해
봅시다. 동시에 다른 어플리케이션을 개발하는데 라이브러리의 버전 업데이트가
필요하다면 어떨까요?

뭐 하고 계신가요? 이럴 때를 위해 ``virtualenv`` 가 있습니다! python
어플리케이션을 위해 독립된 환경을 만들어 줍니다. 글로벌 환경에 라이브러리를 설치 하는 대신 
독립된 환경 안에 Python 라이브러리를 설치 해줍니다.

To install it, just type this command in the shell:
자 그럼 설치해 봅시다. shell에 다음 명령어를 따라 쳐보세요.

.. code:: python

    $ pip install virtualenv

The most important commands are:
중요한 명령어 들은 다음과 같습니다.ㅇ

-  ``$ virtualenv myproject``
-  ``$ source bin/activate``

This first one makes an isolated virtualenv environment in the
``myproject`` folder and the second command activates that isolated
environment.
처음 명령어로 독립된 virtualenv를 ``myproject`` 폴더 안에 만들 었습니다.
그리고 두번째 명령어로 독립된 virtualenv를 실행 시켰습니다.

virtualenv를 만들기 전에 virtualenv가 system의 ``site-packages`` 를 이용하기 
원하는지 혹은 virtualenv의 site-package에 설치하기 원하는지 결정을 해야 합니다.
``virtualenv`` 가 system의 ``site-packages`` 에 접근하길 원한다면 
다음과 같이 ``--system-site-packages`` 를 이용하여 만들수 있습니다.

.. code:: python

    $ virtualenv --system-site-packages mycoolproject

다음과 같이 명령어를 사용하면 ``env`` 를 종료할 수 있습니다.:

.. code:: python

    $ deactivate

Running `python` after deactivating will use your system installation
of Python again. 
`python` 을 실행시킨후 정지시킨다면 system에 설치를 다시 할것입니다???

**Bonus**

bash 나 zsh에서 ``smartcd`` 를 이용한다면 디렉토리를 이동할때 
``virtualenv`` 를 활성화 시키고 비활성화 시키는데 유용하게 작동 할 것입니다.
저는 이것을 좋아하고 잘 사용하고 있습니다. ``smartcd`` 에 대한 더 많은 정보를 
원하신다면 `GitHub <https://github.com/cxreg/smartcd>`__ 에서 찾아 보실 수
있습니다.

이것은 virtualenv에 관한 짧은 소개 글입니다. `이곳
<http://docs.python-guide.org/en/latest/dev/virtualenvs/>`__ 에서 더 많은
정보를 확인 할 수 있습니다.

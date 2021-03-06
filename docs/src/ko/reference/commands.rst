기본 명령어
==============

.. topic:: 고급 개발자가 주목할 사항

    리보그 세상(Reeborg's World)은 파이썬 3 구문(Brython 덕분)과 PEP 8 관례(일부 사소한 예외가 존재함)를 준수한다.

.. topic:: 완전 초급 개발자가 주목할 사항

   *이것이 문제다!* 완전 초보자로, 파이썬 (그리고 프로그래밍)에 관해 어떤 것도 알지 못한다면,
   기본 명령어가 동작하는 방식을 시연하는데 파이썬 구문이 사용될 때 다음에 기술되는 것이 혼란스러울 것이다.
   하지만, 파이썬 구문을 설명하려면, 기본 명령어가 어떤 것인지 여전히 숙지할 필요가 있다...

   저자 추천: 이번 학습교재를 쭉 읽어 내려간다.
   이해가 되지 않는 것이 있다면, 너무 많은 시간은 사용하지 않는다.
   그리고 나서, 다음 페이지를 읽어 나간다.
   리보그 세상에서 발견되는 객체에 관해 먼저 설명하고,
   다음 페이지에서 파이썬에 대한 짧은 소개가 이어지는데, 유사한 예제가 사용된다.
   페이지를 쭉 읽어나간 후에, 여기로 다시 되돌아 온다... 그러고 나면 모든 것이 훨씬 더 이해가 잘 될 것이다.

여기에서, 간단한 세상과 리보그가 따라야 되는 명령어 문서화에 초점을 맞춘다. 명령어는 파이썬 함수다.
파이썬에서, 함수명 다음에 괄호가 붙여 ``my_function()`` 처럼 "호출될" 때, ``my_function`` 이라고 이름 붙은 함수가 실행된다.
거의 말미에 예제 하나를 제외하고, 인자가 없는 함수만 고려한다. [함수에 *인자(argument)* 가 무엇인지 모른다면, 아래에서 설명된다.] 두가지 유형을 고려한다:

1. 리보그가 수행할 수 있는 간단한 동작, 예를 들어 ``move()`` .

2. 리보그가 할 수 있는 정보 수집, 예를 들어 ``front_is_clear()`` 함수는 리보그가 진행하는 경로에 장애물이 있는지 판단하게 한다.

시연할 예제에, 일부 특수 파이썬 키워드가 사용된다.
예를 들어, ``while``, ``True``, ``not`` 키워드는 아직 본적이 없을 수 있다.

이동
--------


``move()``
***********

리보그 세상은 격자에서 정의된다.
리보그 동작은 격자 지점 한곳에서 일어나거나 **혹은**
리보그가 격자 한지점에서 또다른 지점으로 ``move()`` 명령을 받아 이동한다.

=================  =================
``move()`` 이동전  ``move()`` 이동후
-----------------  -----------------
|move_e_before|    |move_e_after|
|move_n_before|    |move_n_after|
|move_w_before|    |move_w_after|
|move_s_before|    |move_s_after|
=================  =================



.. |move_e_before| image:: ../../images/move_e_before.png
.. |move_e_after| image:: ../../images/move_e_after.png
.. |move_n_before| image:: ../../images/move_n_before.png
.. |move_n_after| image:: ../../images/move_n_after.png
.. |move_w_before| image:: ../../images/move_w_before.png
.. |move_w_after| image:: ../../images/move_w_after.png
.. |move_s_before| image:: ../../images/move_s_before.png
.. |move_s_after| image:: ../../images/move_s_after.png

만약 리보그 이동경로가 막히게 되면,
``move()`` 명령은 실패할 수 있고, 프로그램이 멈추게 된다.


``turn_left()``
***************

``turn_left()`` 명령어는 리보그로 하여금 왼쪽으로 90도 회전하게 한다. 이러한 명령어는 절대로 실패할 수 없다.

|turn_left|

.. |turn_left| image:: ../../images/turn_left.gif

객체 다루기
----------------


.. important::

    해당 세상에서, 리보그가 한번에 한가지 유형의 객체만 가진다고 가정한다.

``take()``
************

``take()`` 명령어는 리보그로 하여금 본인이 위치한 지점에 객체를 집어들게 한다. 해당 지점에 어떤 객체도 없다면 명령어는 동작하는 않는다; 두가지 다른 유형의 객체가 있어도 실패할 수 있는데 사유는 어느 객체를 집어할지 모르기 때문이다.

``put()``
************

``put()`` 명령어는 리보그로 하여금 지니고 있는 객체를 바닥에 놓게 명령한다. 리보그가 어떤 객체도 지니고 있지 않다면 동작하지 않는다. 혹은 한가지 유형 이상의 객체를 지니고 있어도 실패하는데 사유는 어느 객체를 바닥에 놓아야 될지 모르기 때문이다.

|take_put|

.. |take_put| image:: ../../images/take_put.gif

세상에 흩어진 정보 수집
--------------------------------------------

리보그가 제한된 감각기관을 가지고 있는데,
그럼에도 불구하고 리보그를 도와서 요구받은 작업을 완수하는데 있어 제한된 감각기관으로도 충분하다.

``is_facing_north()``
**********************

리보그는 북쪽을 향하고(컴퓨터 화면 위쪽) 있는지 아닌지를 판단할 수 있다.

|is_facing_north|

.. |is_facing_north| image:: ../../images/is_facing_north.gif


``at_goal()``
*************

리보그는 최종 목적지에 도착했는지 판단할 수 있다. 최종 목적지는 작업에 나타나 있다.

|at_goal|

.. |at_goal| image:: ../../images/at_goal.gif


``front_is_clear()``
********************

리보그는 진행하는 경로에 (벽같이) 바로 앞에 장애물이 있는지 판단할 수 있다. 다음에 바로 나온 예제에,
``think()`` 도 사용할 수 있는데, 말미에 설명된다.

|think|


``right_is_clear()``
********************

리보그는 우측에 장애물이 있는지 판단할 수 있다.
다음 예제에서, 리보그는 빈틈이 있는 곳까지 우측 벽을 따라 쭉 진행한다. 빈틈이 있는 지점에서, ``build_wall()`` 함수를 사용해서 빈틈을 매꾼다. ``build_wall()`` 함수는 말미에 다시 설명된다.

|build_wall|


``object_here()``
******************

해당 지점에 적어도 객체가 하나 있는지 없는지를 리보그는 판단할 수 있다.

``carries_object()``
**********************

적어도 객체 하나를 지니고 있는지 없는지 리보그는 판단할 수 있다.

다음 예제에서, ``object_here()`` 와 ``carries_object()`` 함수를 모두 사용해서, 리보그로 하여금 모든 객체를 집어서, 다른 지점에 모두 놓도록 지시했다.
해당 지점에 객체가 하나 이상 있다면,
얼마나 많은 객체가 해당 지점에 있는지 숫자가 나타나 있다.

|object_here|

.. |object_here| image:: ../../images/object_here.gif


끼어들기(Interruptions)
------------------------------------

``pause()``
***********

리보그로 하여금 프로그램 해당 지점에서 실행을 멈추게 하고,
재시작하려면 "run" 버튼 혹은 "step" 버튼을 누군가 클릭할 때까지 기다리게 지시한다.

``done()``
***********

코드 나머지 부분을 실행하든, 실행하지 않던, 리보그로 하여금 프로그램을 끝내게 지시한다.

다음 예제에서, ``pause()`` 와 ``done()`` 을 모두 사용해서 정상적인 프로그램 실행에 끼어들어 관여했다.

|pause|

.. |pause| image:: ../../images/pause.gif



``think()``
***********

매번 명령을 수행할 때마다, 약간의 시간을 리보그가 사용한 것을 알아차렸을 수도 있다; 즉, 여러분이 지시한 것에 대해서 "생각해야" 되기 때문이다.
하지만, ``think()`` 함수에 인자를 사용해서 리보그가 생각하는데 걸리는 시간을 변경할 수 있다. 예를 들어::

.. code-block:: python

    think(500)

숫자 ``500`` 가 괄호 사이에 나타나는데, 함수에 전달되는 *인자* 라고 부른다. 숫자가 적을수록, 각 동작을 생각하는데 적은 시간이 든다. 1000 값은 리보그가 생각하는데 1초가 소요됨을 의미한다.
하지만, 리보그는 여러분이 인지하지 못하는 것을 생각할 무언가를 생각해야 되서, 예상한 것보다도 더 오래 생각하는 경우가 있을 수 있다.

|think|

.. |think| image:: ../../images/think.gif



세상 바꾸기
------------------

``build_wall()``
****************

리보그는 앞에서 봤듯이, 본인이 서있는 우측에 벽을 만들 수 있다.
해당 지점에 이미 벽이 있다면, 해당 명령어는 실패함에 주의한다.

|build_wall|

.. |build_wall| image:: ../../images/build_wall.gif

|build_wall_fail|

.. |build_wall_fail| image:: ../../images/build_wall_fail.gif

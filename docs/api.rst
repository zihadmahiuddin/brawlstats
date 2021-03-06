API Reference
=============

.. autoclass:: brawlstats.core.Client
    :members:

Data Models
-----------

.. autoclass:: brawlstats.models.Player
    :members:

.. autoclass:: brawlstats.models.Club
    :members:

.. autoclass:: brawlstats.models.PartialClub
    :members:

.. autoclass:: brawlstats.models.Leaderboard
    :members:

.. autoclass:: brawlstats.models.Events
    :members:

.. autoclass:: brawlstats.models.Constants
    :members:

.. autoclass: brawlstats.models.MiscData
    :members:

Player
-------

A full player object (all its statistics)


Attributes:

============================ ==============================
Name                         Type
============================ ==============================
``tag``                      str
``name``                     str
``name_color_code``          str
``brawlers_unlocked``        int
``brawlers``                 List[\ `Brawler`_, `Brawler`_]
``victories``                int
``solo_showdown_victories``  int
``duo_showdown_victories``   int
``total_exp``                int
``exp_level``                int
``exp_fmt``                  str
``trophies``                 int
``highest_trophies``         int
``avatar_id``                int
``avatar_url``               str
``best_time_as_big_brawler`` str
``best_robo_rumble_time``    str
``has_skins``                bool
``club``                     `PartialClub`_
============================ ==============================

Club
----

A full club object to get a club's statistics. In order to get this, you
must get it from the client or a player object.


Attributes:

===================== ============================
Name                  Type
===================== ============================
``tag``               str
``name``              str
``status``            str
``members_count``     int
``online_members``    int
``trophies``          int
``required_trophies`` int
``description``       str
``badge_id``          int
``badge_url``         str
``members``           List[\ `Member`_, `Member`_]
===================== ============================

PartialClub
-----------

Only returns some statistics of the club. You are returned this via
`Profile`_.club To get a full club, use await `Profile`_.get_club()


Attributes

===================== ====
Name                  Type
===================== ====
``name``              str
``tag``               str
``role``              str
``trophies``          int
``required_trophies`` int
``members``           int
``badge_id``          int
``badge_url``         str
``members``           int
``online_members``    int
===================== ====

Member
------

Returns some info about a club member. Get this by accessing
`Club`_.members

.. code:: py

   members = club.members
   print(members[0].name, members[0].role) # prints best player's name and role (sorted by trophies)

Attributes:

=================== ====
Name                Type
=================== ====
``tag``             str
``name``            str
``name_color_code`` str
``role``            str
``trophies``        int
``avatar_id``       int
``avatar_url``      str
=================== ====

Leaderboard
-----------

Returns a list of top players, clubs, or brawlers. To access this, do ``lb[index]``

Player attributes:

=================== ====
Name                Type
=================== ====
``tag``             str
``name``            str
``name_color_code`` str
``position``        int
``trophies``        int
``club_name``       str
``exp_level``       int
``avatar_id``       int
``avatar_url``      str
=================== ====

Club attributes:

================= ====
Name              Type
================= ====
``tag``           str
``name``          str
``position``      int
``trophies``      int
``members_count`` int
``badge_id``      int
``badge_url``     str
================= ====

Brawler attributes:

=================== ====
Name                Type
=================== ====
``tag``             str
``name``            str
``name_color_code`` str
``position``        int
``trophies``        int
``club_name``       str
``exp_level``       int
``avatar_id``       int
``avatar_url``      str
``rank``            int
=================== ====

Brawler
-------

Returns a brawler object with the following attributes. You can retrieve
a profile’s brawler info by getting `Profile`_.brawlers

.. code:: py

   brawlers = profile.brawlers
   top_brawler = brawlers[0] # first index in list = highest trophies
   print(top_brawler.name, top_brawler.trophies) # prints best brawler's name and trophies

Attributes:

==================== =============================
Name                 Type
==================== =============================
``name``             str
``has_skin``         bool
``skin``             None if no skin otherwise str
``trophies``         int
``highest_trophies`` int
``power``            int
==================== =============================

Events
------

Returns a result of current and upcoming events.

Attributes:

============ ===================
Name         Type
============ ===================
``current``  List[\Event, Event]
``upcoming`` List[\Event, Event]
============ ===================

Event Attributes:

========================= ====
Name                      Type
========================= ====
``slot``                  int
``slot_name``             str
``start_time``            str
``end_time``              str
``start_time_in_seconds`` int
``end_time_in_seconds``   int
``map_name``              str
``map_image_url``         str
``map_id``                int
``game_mode``             str
``free_keys``             int
``has_modifier``          bool
``modifier_name``         str
``modifier_id``           int
========================= ====

Misc Data
---------

Returns misc data such as shop and season info.

Attributes:

===================================== ====
Name                                  Type
===================================== ====
``time_until_season_end_in_seconds``  int
``time_until_season_end``             str
``time_until_shop_reset_in_seconds``  int
``time_until_shop_reset``             str
``server_date_year``                  int
``server_date_day_of_year``           int
===================================== ====



.. _Club: https://brawlstats.readthedocs.io/en/latest/api.html#id1
.. _PartialClub: https://brawlstats.readthedocs.io/en/latest/api.html#id2
.. _Brawler: https://brawlstats.readthedocs.io/en/latest/api.html#id6
.. _Member: https://brawlstats.readthedocs.io/en/latest/api.html#id4
.. _Profile: https://brawlstats.readthedocs.io/en/latest/api.html#profile
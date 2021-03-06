.. _process_list:

=============
Process List
=============

This page describes Percona changes to both the standard |MySQL| ``SHOW PROCESSLIST`` command and the standard |MySQL| ``INFORMATION_SCHEMA`` table ``PROCESSLIST``.

Version Specific Information
============================

  * :rn:`5.7.10-1`:

    * Feature ported from |Percona Server| 5.6

INFORMATION_SCHEMA Tables
=========================

.. table:: INFORMATION_SCHEMA.PROCESSLIST

   This table implements modifications to the standard |MySQL| ``INFORMATION_SCHEMA`` table ``PROCESSLIST``.

   :column ID: The connection identifier.
   :column USER: The |MySQL| user who issued the statement.
   :column HOST: The host name of the client issuing the statement.
   :column DB: The default database, if one is selected, otherwise NULL.
   :column COMMAND: The type of command the thread is executing.
   :column TIME: The time in seconds that the thread has been in its current state.
   :column STATE: An action, event, or state that indicates what the thread is doing.
   :column INFO: The statement that the thread is executing, or NULL if it is not executing any statement.
   :column TIME_MS: The time in milliseconds that the thread has been in its current state.
   :column ROWS_EXAMINED: The number of rows examined by the statement being executed (*NOTE:* This column is not updated for each examined row so it does not necessarily show an up-to-date value while the statement is executing. It only shows a correct value after the statement has completed.).
   :column ROWS_SENT: The number of rows sent by the statement being executed.
   :column ROWS_READ: The number of rows read by the statement being executed.


Example Output
==============

Table :table:`PROCESSLIST`: ::

  mysql> SELECT * FROM INFORMATION_SCHEMA.PROCESSLIST;

  +----+------+-----------+--------------------+---------+------+-----------+---------------------------+---------+-----------+---------------+
  | ID | USER | HOST      | DB                 | COMMAND | TIME | STATE     | INFO                      | TIME_MS | ROWS_SENT | ROWS_EXAMINED |
  +----+------+-----------+--------------------+---------+------+-----------+---------------------------+---------+-----------+---------------+
  | 12 | root | localhost | information_schema | Query   |    0 | executing | select * from processlist |       0 |         0 |             0 |
  +----+------+-----------+--------------------+---------+------+-----------+---------------------------+---------+-----------+---------------+


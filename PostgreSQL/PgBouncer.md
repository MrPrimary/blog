**PgBouncer is a lightweight connection pooler for PostgreSQL.**
**pgbouncer** is a PostgreSQL connection pooler. Any target application can be connected to **pgbouncer** as if it were a PostgreSQL server, and **pgbouncer** will create a connection to the actual server, or it will reuse one of its existing connections.

The aim of **pgbouncer** is to lower the performance impact of opening new connections to PostgreSQL.

In order not to compromise transaction semantics for connection pooling, **pgbouncer** supports several types of pooling when rotating connections:

**Session pooling**:
Most polite method. When client connects, a server connection will be assigned to it for the whole duration the client stays connected. When the client disconnects, the server connection will be put back into the pool. This is the default method.

**Transaction pooling**:
A server connection is assigned to client only during a transaction. When PgBouncer notices that transaction is over, the server connection will be put back into the pool.

**Statement pooling**:
Most aggressive method. The server connection will be put back into pool immediately after a query completes. Multi-statement transactions are disallowed in this mode as they would break.

The administration interface of **pgbouncer** consists of some new SHOW commands available when connected to a special “virtual” database **pgbouncer**.


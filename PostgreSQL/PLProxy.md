
### <font color=orange size=4 >Project Overview</font>
---
PL/Proxy is database partitioning system implemented as PL language. Main idea is that proxy function will be created with same signature as remote function to be called, so only destination info needs to be specified inside proxy function body.

### <font color=orange size=4 >Project Status</font>
---
Stable, in production.

### <font color=orange size=4 >Features</font>
---
* PL/Proxy functions detect remote functions to be called from their own signature.
* Function can be run on one, some or all members of the cluster.
* If query is executed on several partitions, it will happen in parallel.
* Queries are run in auto-commit mode on the remote server.
* Query parameters are sent separately from query body, thus avoiding quoting/unquoting overhead on both sides.
* Does not contain code connection pooling, works with external pooler if needed, preferably PgBouncer.

### <font color=orange size=4 >Documentation</font>
---
* Language [syntax](https://plproxy.github.io/syntax.html).
* Cluster [config](https://plproxy.github.io/config.html) functions.
* [FAQ](https://plproxy.github.io/faq.html), describes few design decisions.
* Official [tutorial](https://plproxy.github.io/tutorial.html)
* Kristo Kaiv's tutorial: [part 1](http://kaiv.wordpress.com/2007/07/27/postgresql-cluster-partitioning-with-plproxy-part-i/), [part 2](http://kaiv.wordpress.com/2007/09/02/postgresql-cluster-partitioning-with-plproxy-part-ii/).

### <font color=orange size=4 >Downloads</font>
---
* Source releases: https://plproxy.github.io/
* GIT: https://github.com/plproxy/plproxy

**Binary packages (may not be up-to-date)**
* Deb: PL/Proxy is included in [Debian](http://www.debian.org/) and [Ubuntu](http://www.ubuntu.com/) official repositories as postgresql-X.Y-plproxy package, where X.Y is postgres major version.
* RPM: [PGDG Yum repository](http://yum.postgresql.org/)

### <font color=orange size=4 >Community Support</font>
---
* Discussion: https://gitter.im/plproxy/plproxy
* Bugtracker: https://github.com/plproxy/plproxy/issues

### <font color=orange size=4 >Quick Examples</font>
---
#### <font color=orange size=3 >Simple remote function call</font>
Connect to database "users" on localhost and call SQL function there: **SELECT * FROM get_user_email($1);**
``` 
CREATE FUNCTION get_user_email(username text) RETURNS text AS $$

   CONNECT 'dbname=users';
 
$$ LANGUAGE plproxy;
```
#### <font color=orange size=3 >Partitioned remote function call</font>
Users are spread over several databases, partition number is acquired by taking **hashtext(username)**. This needs also configuring the cluster, described in documentation. After this is done, actual proxy function looks following:
```
CREATE FUNCTION get_user_email(username text) RETURNS text AS $$

   CLUSTER 'userdb';
   RUN ON hashtext(username);

$$ LANGUAGE plproxy;
```


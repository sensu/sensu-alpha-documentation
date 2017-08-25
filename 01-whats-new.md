# What's new in Sensu 2.0?

## Simplified Transport

RabbitMQ did a lot of great things for Sensu 1.0. The AMQP is the gold standard
in messaging broker protocols. We learned a great deal from that experience, 
and we’re bring it along with us to Sensu 2.0. The conceptual model of the new 
Sensu transport is very much inspired by AMQP’s transport model, and Pub/Sub is 
still at the heart of how Sensu works.

Sensu 2.0 is using WebSockets to communicate between the agent (the sensu client) 
and the backend.

WebSockets use a framed protocol, much like AMQP. Unlike AMQP, however, the data 
within a WebSocket frame is either “binary” or “ascii”. We mark all of our data 
frames as binary to avoid encoding issues, and the messages we send of WebSockets 
are simply JSON message bodies, just like Sensu 1.0. WebSockets give us bidirectional 
streaming over HTTPS without needing an intermediate broker, and they’re readily 
supported in many languages.

## Configuration and Data

While Redis has served us well as our data storage for some time, we need storage 
that offers us strong persistence and consistency guarantees. Redis is being 
replaced by [Etcd](https://coreos.com/etcd). Etcd is a high-performance, distributed 
NoSQL key-value store. It’s commercially supported by CoreOS and a healthy community 
of developers. It is also the cornerstone of some major projects including Kubernetes
and Container Linux. Etcd is embedded in Sensu 2.0. There is no need to run an external 
Etcd cluster.

All configuration data is now stored inside Etcd. All config files that had to be 
reified on disk (e.g. by configuration management) are now serialized into Etcd.
Etcd is responsible for replicating all of this to other Sensu servers using the 
[Raft](https://raft.github.io/) consensus protocol.

Etcd can lose just under half of the cluster and still function. Total machine failure 
of half the cluster simultaneously would be required to necessitate a restore from backup.
Etcd allows you to take snapshots, those snapshots can be backed up to a third-party 
location, and restoring from a snapshot doesn’t store cluster state, so they can be used 
to seed new clusters as well.

## Sensu 2.0 API and RBAC

Sensu 2.0 can be completely controlled via the API. Everything that was in a file is now 
configurable via the API. This includes checks, handlers, and mutators. You can still use 
CM to control Sensu’s configuration, but now you have plenty of other options as well.

The API requires authentication. We create a default admin user `admin` with the password
`P@ssw0rd!` you can use for your first login to the API. This user can be used to create
additional users for yourself and other users within your organization. You also now
have the ability to create and manage roles for users with Sensu 2.0's role-based access
control (RBAC) capabilities.

Sensu 2.0 is based around namespaces we call "organizations." Organizations uniquely identify 
sets of objects in Sensu. Roles can be used to control access to resources. Users can have 
multiple roles granting them different levels of access to different kinds of objects in 
different organizations. For example, your ops teams can create a read-only role for all of 
their resources that they then grant to other teams. And, of course, you can have checks with 
the same name in different organizations/environments


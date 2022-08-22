# FAQ

### Images aren't send to the panel. How to fix?

First check if you don't get any errors. **If not, make sure the name of the ActionFoto board is also the name of a ThemePark ride.**&#x20;

If you get an error, please check below.

### I get an `PacketTooBigException`.

The error looks like this:

```bash
com.mysql.jdbc.PacketTooBigException: Packet for query is too large. You can change this value on the server by setting the max_allowed_packet' variable.
```

As you can see, you have to change the max\_allowed\_packet setting.

Open the my.cnf file and change **max\_allowed\_packet** from **32M** to **256M**. This will allow us to send bigger images.

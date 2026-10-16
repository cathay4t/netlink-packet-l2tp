# netlink-packet-l2tp

L2TP generic netlink packet definitions for the
[rust-netlink](https://github.com/rust-netlink) project.

This crate only parses and emits the netlink payload of the `l2tp` generic
netlink family (`include/uapi/linux/l2tp.h` in the Linux kernel). To talk to
the kernel, use the `nl-l2tp` crate.

```rust,no_run
use netlink_packet_l2tp::{
    L2tpAttribute, L2tpCmd, L2tpEncapType, L2tpMessage,
};

let message = L2tpMessage {
    cmd: L2tpCmd::TunnelCreate,
    attributes: vec![
        L2tpAttribute::ConnId(1000),
        L2tpAttribute::PeerConnId(2000),
        L2tpAttribute::ProtoVersion(3),
        L2tpAttribute::EncapType(L2tpEncapType::Udp),
    ],
};
```

License: MIT

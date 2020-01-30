# PJLink

PJLink is an overlay of the TCP protocol, used to communicate with video projectors. More info [here](https://pjlink.jbmia.or.jp/english/).

![The parameters for this module are almost the same as the TCP Client.](../../.gitbook/assets/pjlink.png)

## Parameters

Because it's a slightly modified TCP Client module, you can check the docs for the parameters on the [TCP Client](tcp-client.md) page.

**Password :** You can here specify if need be the password that is set up in the projector's PJLink settings.

The remote port is by default set up to the default PJLink port setting that is 4352. You can change that if that's not the port set up in the projector.

There are already precreated values who will be updated when the projector sends back informations about its status.

{% hint style="info" %}
Not all the PJLink specification is supported by this module, more support will come when the community asks for it, and when I get time to implement it \(make [donations](https://github.com/sponsors/benkuper) !\)
{% endhint %}




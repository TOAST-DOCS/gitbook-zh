## Compute > Bare Metal Instance > Console User Guide

## Create Instance
Creating a bare metal instance is the same as creating a normal instance, except for the notes below when creating a bare metal instance.

For more information, see [Instance Overview](/Compute/Instance/en/overview).

### Notes when creating a bare metal instance

* It takes about 30 minutes to create a bare metal instance.
* Bare metal instances are provided with local block storage. The local block storage type is `SSD`, and capacity cannot be increased or decreased separately.
* Bare metal instances cannot create and attach additional block storage.
* Bare metal instances are charged from the moment they are created.
* Bare metal instances are charged even when stopped.

> [Caution] In the event of a hardware failure, the user instance may be provided in the same state as when it was created, and in this case, the data may be lost and cannot be recovered.
NHN Cloud is not responsible for data loss due to service failure. Therefore, separate backup or duplication is recommended.






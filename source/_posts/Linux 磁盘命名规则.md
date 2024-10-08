1. **IDE硬盘**：早期的 IDE 接口硬盘被命名为`hd[a-d]`，其中 `hd` 表示硬盘（Hard Disk），后面的字母 `a` 至 `d` 代表系统中第一至第四个 IDE 硬盘。不过，随着 SATA 接口硬盘的普及，这种命名方式已经变得不那么常见。

2. **SATA/SCSI硬盘**：这类硬盘被命名为 `sd[a-z]`，`sd` 代表 SCSI 盘，尽管 SATA 硬盘并不直接使用 SCSI 接口，但 Linux 内核通过 SCSI 子系统来处理这些设备，因此也使用 `sd` 作为前缀。后续的字母代表不同的硬盘，例如 `sda` 是第一个 SATA/SCSI 硬盘，`sdb` 是第二个，依此类推。当超过 26 个硬盘时，命名会使用多个字母，如 `sdaa`、`sdab` 等。

3. **NVMe硬盘**：随着 NVMe 接口硬盘的出现，Linux 采用了新的命名规则，即 `nvme[0-9]n[1-9]`，其中 `nvme` 是固定的前缀，第一个数字表示控制器的编号，`n` 是固定字符，第二个数字表示该控制器下的命名空间编号。例如，`nvme0n1` 表示第一个 NVMe 控制器下的第一个命名空间，即第一个 NVMe 硬盘。

4. **分区**：Linux 中的磁盘分区也遵循一定的命名规则。对于 IDE、SATA 和 SCSI 硬盘，分区被表示为硬盘名称后跟一个数字，例如 `sda1`、`sda2` 等，分别表示 `sda` 硬盘的第一和第二个分区。对于 NVMe 硬盘，分区命名在硬盘名之后直接加上分区号，例如 `nvme0n1p1`、`nvme0n1p2`，分别代表 `nvme0n1` 硬盘的第一和第二个分区。
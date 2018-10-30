---
layout: "post"
title: "Enable login root melalui SSH"
date: "2018-10-30 13:01"
category: "centos"
---
Beberapa kali saya gagal login ke ssh VM melalui terminal dilaptop. Satu-satu akses masuk saya adalah melalui ssh Web base yang disediakan oleh penyedia layanan VPS yang saya gunakan.

Ternyata pada beberapa vm, kita tidak dapat langsung mengakses vm tersebut kecuali SSH web base bawaan karena pengaturan pada file `sshd_config` belum diatur. Agak sedikit merepotkan, sehingga perlu dilakukan pengaturan dengan cara berikut ini :

- Sebagai root, masuklah ke file `sshd_config` menggunakan text editor. File `sshd_config` dapat ditemukan pada direktori

```
/etc/ssh/sshd_config
```
- Temukan baris kode `PermitRootLogin`. Ubahlah nilai baris tersebut menjadi `yes` sehingga pengaturannya menjadi seperti berikut ini

```
# Authentication:
#LoginGraceTime 2m
PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10
```
- Temukan juga baris kode `PasswordAuthentication`. Ubahlah nilai baris kode tersebut menjadi `yes`

```
PasswordAuthentication yes
```

- Save, lalu restart service ssh

```
service sshd restart
```

Selesai.

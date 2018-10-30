---
layout: "post"
title: "Menambahkan sudo user pada CentOS"
date: "2018-10-30 13:45"
category: centos
---
Perintah `sudo` tersedia pada sistem operasi linux sebagai sebuah mekanisme hak akses user biasa agar dapat mengakses dan mengeksekusi file yang hanya bisa diakses oleh `root`.

Untuk menambahkan sebuah user agar bisa menggunakan perintah `sudo` dapat dilakukan dengan langkah berikut ini :

- Tentukan user yang akan ditambahkan. Jika user yang akan ditambahkan belum ada, dapat dilakukan create user terlebih dahulu.

Catatan : pastikan mengganti `username` dengan nama username yang diinginkan.

```
adduser `username`
```

Selanjutnya, gunakan perintah `passwd` untuk merubah password `username` yang baru saja dibuat.

```
passwd username
```
Selanjutnya akan muncul isian untuk melakukan perubahan password.

```
Set password prompts:
Changing password for user username.
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
```
- Selanjutnya dengan menggunakan perintah `usermod` ditambahkan `username` yang telah dibuat kedalam group `wheel`. Pada CentOS, seluruh user yang berada pada group `wheel` memiliki hak akses untuk menjalankan perintah `sudo`.

```
usermod -aG wheel username
```

- Setelah selesai, cobalah melakukan testing pada user yang telah ditambahkan. Misalnya dengan menjalankan perintah berikut :

```
sudo su
```

1) Материалы курса - https://confluence.globallogic.com/display/INOB/Linux+Kernel
2) Инструкции по сборке и запуску - ниже.
3) Нужно выслать мне скриншот с выводом uname -a

Если кого-то забыл - сообщите пожалуйста.
Жду всех в пятницу :)

Спасибо,
Андрей


==============================
Интсрукция по сборке ядра

1) Скачать последнюю версию  ядра из kernel.org
2) Распаковать: tar xf linux-3.5.3.tar.bz2
3) Отконфигурировать по умолчанию: make defconfig
4) Запустить make menuconfig и выбрать седующие дополнительные опции:
- Device Drivers  ---> [*] Block devices  ---> [*]   Very old hard
disk (MFM/RLL/IDE) driver
- Kernel hacking  ---> Compile the kernel with debug info
5) Выполнить make либо make bzImage
6) Должен появиться файл arch/x86/boot/bzImage

7) для пользователей 64-битных систем - все команды make выполнять с
флагом ARCH=i386:
make ARCH=i386 defconfig
make ARCH=i386 menuconfig
make ARCH=i386

===============================================
Запуск qemu

1) Скачать архив файловой системы
https://docs.google.com/a/globallogic.com/file/d/0ByIIdoxV3FKCbDR6VjdwR01iQm8/edit
2) Создать пустой образ диска: dd if=/dev/zero of=hdd.img bs=1M count=1024
3) Отформатировать: /sbin/mkfs.ext3 hdd.img

Следующие  действия из-под root:
4) Создать временную директорию: mkdir hdd
5) Примонтировать образ: mount -o loop hdd.img hdd
6) Скопировать скачанную файловую систему
7) Отмонтировать: umount hdd

Опять из-под обычного пользователя:
8) Запустить qemu:
qemu -m 128M -kernel arch/x86/boot/bzImage -append "root=/dev/sda" -hda hdd.img

================================

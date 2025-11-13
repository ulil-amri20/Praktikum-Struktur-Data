Implementasi Queue di Python

Program ini menunjukkan contoh sederhana struktur data Queue (antrian) menggunakan **list** di Python.  
Queue bekerja dengan prinsip FIFO (First In, First Out) — elemen yang pertama masuk akan menjadi yang pertama keluar.

Kode Program :

```python
queue = []

# Enqueue
queue.append('A')
queue.append('B')
queue.append('C')
print("Queue: ", queue)

# Dequeue
element = queue.pop(0)
print("Dequeue: ", element)

# Peek
frontElement = queue[0]
print("Peek: ", frontElement)

# isEmpty
isEmpty = not bool(queue)
print("isEmpty: ", isEmpty)

# Size
print("Size: ", len(queue))
```

Penjelasan

1).inisialisasi Queue
   Membuat list kosong sebagai antrian:

   ```python
   queue = []
   ```

2).Enqueue (Menambah Data)
   Menambahkan elemen ke dalam antrian menggunakan `append()`:

   ```python
   queue.append('A')
   queue.append('B')
   queue.append('C')
   ```

   Setelah bagian ini, isi antrian: `['A', 'B', 'C']`.

3).Dequeue (Menghapus Data Terdepan)
   Menghapus elemen pertama dengan `pop(0)`:

   ```python
   element = queue.pop(0)
   ```

   Elemen `'A'` keluar dari antrian.

4).Peek (Melihat Elemen Terdepan)
   Melihat isi paling depan tanpa menghapus:

   ```python
   frontElement = queue[0]
   ```

5).isEmpty (Cek Kosong atau Tidak)
   Mengecek apakah antrian kosong:

   ```python
   isEmpty = not bool(queue)
   ```

6).Size (Jumlah Elemen)
   Menghitung banyaknya elemen yang tersisa:

   ```python
   len(queue)
   ```

Hasil Eksekusi :

```
Queue:  ['A', 'B', 'C']
Dequeue:  A
Peek:  B
isEmpty:  False
Size:  2
```

Kesimpulan :

Queue di Python bisa dibuat dengan `list`.
Prinsip kerjanya adalah FIFO (First In, First Out).
Operasi dasar:

`append()` → menambah data (enqueue)
`pop(0)` → menghapus data paling depan (dequeue)
`queue[0]` → melihat data paling depan (peek)
Struktur ini berguna untuk simulasi antrian pelanggan, sistem printer, atau proses data berurutan.

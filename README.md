# Web_Scraping_Pesona_JNE
Web Scraping Data Produk Pesanan Oleh-oleh Nusantara JNE

PESONA merupakan layanan pengiriman makanan kuliner khas Indonesia tanpa harus pergi ke daerah asalnya. Pilihan makanan dari beberapa daerah di Indonesia yang kami tawarkan sudah melalui seleksi kelayakan dan masa uji coba selama hampir setahun sehingga aman untuk dikonsumsi oleh pelanggan.

Kali ini saya mencoba untuk mengambil data produk terbaru dari website Pesona JNE dengan menggunakan library BeautifulSoup

Total produk terbaru dari Pesona JNE terdapat 60 Varian,
Data yang diambil adalah Nama, Vendor dan Price. 

Welcome to the Web_Scraping_Pesona_JNE wiki!

```python
import requests
import pandas as pd
from bs4 import BeautifulSoup
from pprint import pprint
```


```python
url = 'https://www.pesonanusantara.co.id/'
data = requests.get(url)
#print(data.text)
```

```python
my_data = []

html = BeautifulSoup(data.text, 'html.parser')
products = html.select('li.item')

for product in products:
    
    name = product.select('.product-name')[0].get_text()
    vendor = product.select('.vendor')[0].get_text()
    price = product.select('.price')[0].get_text()
    
    my_data.append({
        'name':name,
        'vendor':vendor,
        'price':price
    })
    
pprint(my_data)
```

    [{'name': 'BROWKIES RUMPUT LAUT (ISI 3 PACK)',
      'price': ' Rp 45.000',
      'vendor': "D'Ipey - Makassar "},
     {'name': 'Sambal Goreng Ikan Asin Toples',
      'price': ' Rp 45.000',
      'vendor': 'Mickey Mouse - Banjarmasin '},
     {'name': 'DENDENG AYAM SLICE KUKURUYUK MAKANAN SIAP SAJI ORIGINAL - 200 GRAM',
      'price': ' Rp 75.000',
      'vendor': 'Dendeng Kukuruyuk - Bandung '},
     {'name': 'Kemplang Goreng Cumi 1/2 Kilo',
      'price': ' Rp 96.000',
      'vendor': 'Toko Lck - Pangkal Pinang '},
     {'name': 'Picnic Roll Beef',
      'price': ' Rp 81.700',
      'vendor': 'CV. Prima Rasa - Bandung '},
     {'name': 'FISH SKIN ORIGINAL FOOD MATANG (ISI 2 PACK @250GR)',
      'price': ' Rp 50.000',
      'vendor': 'Raja Patin - Medan '},
     {'name': 'SAMBEL SEBLAK TIDAK PEDAS ISI 5 BOTOL',
      'price': ' Rp 75.000',
      'vendor': 'Nu Ibun - Bandung '},
     {'name': 'TEKWAN RUMPUT LAUT',
      'price': ' Rp 75.000',
      'vendor': "Khaniya's Frozen - Bontang "},
     {'name': 'TEH DAUN TIN (ISI 25 PCS)',
      'price': ' Rp 25.000',
      'vendor': 'Zahra Florist - Bontang '},
     {'name': 'Papapia Kacang Hijau',
      'price': ' Rp 42.000',
      'vendor': 'Papapia - Bogor '},
     {'name': 'MINYAK SEREH 60 ML',
      'price': ' Rp 85.000',
      'vendor': 'T. Orens - Makasar '},
     {'name': 'KERIPIK BAWANG',
      'price': ' Rp 22.000',
      'vendor': 'Delis Delen - Cilegon '},
     {'name': 'Wedang Jahe Secang',
      'price': ' Rp 12.500',
      'vendor': 'Yopi Homade - Cilegon '},
     {'name': 'Toarco Toraja Powder',
      'price': ' Rp 69.000',
      'vendor': 'Toarco Toraja - Makasar '},
     {'name': 'KULIT PASTRY/PUFF PASTRY',
      'price': ' Rp 31.500',
      'vendor': 'Kanung Bakery - Bogor '},
     {'name': 'Sambal Cabe Ijo (Isi 2 botol)',
      'price': ' Rp 60.000',
      'vendor': 'Bridechili - Bogor  '},
     {'name': 'Kemplang Goreng I / Udang',
      'price': ' Rp 52.500',
      'vendor': 'Yunna Snack - Pangkal Pinang '},
     {'name': 'JAHE INSTAN PLUS REMPAH 250 GR',
      'price': ' Rp 35.000',
      'vendor': 'Rumah Berkah - Yogyakarta '},
     {'name': 'COKLAT METE', 'price': ' Rp 25.000', 'vendor': 'Athifah - Kendari '},
     {'name': 'Keripik Pisang Keju (isi 3 bungkus)',
      'price': ' Rp 45.000',
      'vendor': 'Mekarsari - Kediri '},
     {'name': 'KUE BAWANG',
      'price': ' Rp 10.000',
      'vendor': 'Turunan Cabe - Medan'},
     {'name': 'ABON EBI', 'price': ' Rp 15.000', 'vendor': 'Turunan Cabe - Medan'},
     {'name': 'SAOS CABE 140ML',
      'price': ' Rp 10.000',
      'vendor': 'Turunan Cabe - Medan'},
     {'name': 'KACANG INTIP MANIS GURIH',
      'price': ' Rp 10.000',
      'vendor': 'Cahaya Syajaril - Medan'},
     {'name': 'MANISAN CABAI',
      'price': ' Rp 15.000',
      'vendor': 'Cahaya Syajaril - Medan'},
     {'name': 'MUSHOME CHIPS NORI SALTED EGG',
      'price': ' Rp 30.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'MUSHOME CHIPS NORI ORIGINAL',
      'price': ' Rp 25.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'MUSHOME CHIPS BBQ',
      'price': ' Rp 20.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'MUSHOME CHIPS JAGUNG BAKAR',
      'price': ' Rp 20.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'MUSHOME CHIPS KEJU',
      'price': ' Rp 20.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'MUSHOME CHIPS PEDAS',
      'price': ' Rp 20.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'MUSHOME CHIPS JAMUR ORIGINAL',
      'price': ' Rp 20.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'GEPUK PLANT BASED 150GR',
      'price': ' Rp 45.000',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'DENDENG PEDAS PLANT BASED 150GR',
      'price': ' Rp 57.000',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'DENDENG MANIS PLANT BASED 150GR',
      'price': ' Rp 55.000',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'RENDANG PLANT BASED 250GR',
      'price': ' Rp 75.500',
      'vendor': 'Meatless Kingdom - Bandung'},
     {'name': 'KARTIKA TOAST HAMPERS MINI PACK',
      'price': ' Rp 100.000',
      'vendor': 'Paket Hampers Kartika Inti Sejati - Bandung'},
     {'name': 'KARTIKA TOAST HAMPERS REGULER 5S',
      'price': ' Rp 240.000',
      'vendor': 'Paket Hampers Kartika Inti Sejati - Bandung'},
     {'name': 'KARTIKA TOAST HAMPERS REGULER 3S',
      'price': ' Rp 140.000',
      'vendor': 'Paket Hampers Kartika Inti Sejati - Bandung'},
     {'name': 'Java Mocha Robusta Temanggung',
      'price': ' Rp 28.000',
      'vendor': 'PESONA Express'},
     {'name': 'BOLU MERANTI STANDAR KEJU',
      'price': ' Rp 95.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'Pempek Candy Paket 1',
      'price': ' Rp 110.000',
      'vendor': 'Pempek Candy - Palembang'},
     {'name': 'Tahu Bakso',
      'price': ' Rp 42.000',
      'vendor': 'Tahu Bakso Bu Pudji - Semarang'},
     {'name': 'BOLU MERANTI TOPPING KEJU',
      'price': ' Rp 115.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'Kripik Balado Kristine Hakim 500Gr',
      'price': ' Rp 50.000',
      'vendor': 'Toko Kristin Hakim - Padang'},
     {'name': 'Pempek Candy Paket 2',
      'price': ' Rp 165.000',
      'vendor': 'Pempek Candy - Palembang'},
     {'name': 'Pempek Candy Paket 3',
      'price': ' Rp 220.000',
      'vendor': 'Pempek Candy - Palembang'},
     {'name': 'Brownis Amanda Original Coklat',
      'price': ' Rp 43.000',
      'vendor': 'Brownies Amanda - Bandung'},
     {'name': 'BOLU MERANTI STANDARD MOCCA',
      'price': ' Rp 85.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'Bika Ambon Original',
      'price': ' Rp 86.000',
      'vendor': 'Zulaikha - Medan'},
     {'name': 'Bolu Meranti Topping Meses Keju',
      'price': ' Rp 115.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'KUE KERANJANG SPECIAL ISI 3PCS',
      'price': ' Rp 20.000',
      'vendor': 'Kue Keranjang - Jakarta'},
     {'name': 'Pempek Vico Isi 35',
      'price': ' Rp 110.000',
      'vendor': 'Pempek Vico - Palembang'},
     {'name': 'BOLU MERANTI TOPPING MESES MOCCA',
      'price': ' Rp 105.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'Bolu Meranti Topping Keju Isi Keju',
      'price': ' Rp 115.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'Batagor Kingsley (Isi 10pcs-Matang)',
      'price': ' Rp 145.000',
      'vendor': 'Batagor Kingsley - Bandung'},
     {'name': 'BOLU MERANTI STANDARD KEJU',
      'price': ' Rp 95.000',
      'vendor': 'Meranti - Medan'},
     {'name': 'Molen Pisang Coklat Keju Mini',
      'price': ' Rp 65.000',
      'vendor': 'Kartika Sari - Bandung'},
     {'name': 'Picnic Roll Beef',
      'price': ' Rp 81.700',
      'vendor': 'CV. Prima Rasa - Bandung'},
     {'name': 'Sambal Bawang Bu Rudy (Isi 2)',
      'price': ' Rp 54.000',
      'vendor': 'Sambal Bu Rudi - Surabaya'}]
    


```python
df = pd.DataFrame(my_data)
df.to_csv('Data_Pesona.csv')
```

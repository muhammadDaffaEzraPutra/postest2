# postest2
#Muhammad Daffa Ezra Putra
#2309116052
#Sistem Informasi B


from prettytable import PrettyTable

# list untuk menyimpan data item
data_item = [
    [1, "bibit selada", "9000", 60],
    [2, "bibit tomat", "12000", 40],
    [3, "bibit pakcoy", "10.000", 35],
    [4, "bibit cabe", "16.000", 15],
    [5, "bibit wortel", "14000", 24]
]


# pembeli
def transaksi():
    while True:
        # menampilkan seluruh item yang tersedia
        print("Daftar Item yang Tersedia")
        show_item()

        # input id item dan jumlah yang ingin dibeli
        id_item = int(input("Masukkan ID item yang ingin dibeli: "))
        qty = int(input("Masukkan jumlah yang ingin dibeli: "))

        #hasil jumlah barang
        # menampilkan total harga
        for i in range(len(data_item)):
                harga_item = int(data_item[i][2])
                if data_item[i][0] == id_item:
                    total_harga = harga_item * qty
                    print("Total harga: Rp", total_harga)
                    return

        # memeriksa apabila jumlah yang ingin dibeli melebihi stok
        for item in data_item:
            if item[0] == id_item:
                if qty > item[10]:
                    print("Maaf, jumlah stok item tidak mencukupi!")
                    break
                else:
                    total_harga = item[10] * qty
                    print(f"Total harga: Rp {total_harga}")
                    item[10] -= qty
                    return
        else:
            # menampilkan kembali tampilan daftar item apabila input salah
            print("Maaf, item tidak ditemukan")


# admin
def create():
    # input data item yang baru
    id_item = len(data_item) + 1
    nama_item = input("Masukkan nama item: ")
    harga_item = int(input("Masukkan harga item: "))
    stok_item = int(input("Masukkan stok item: "))
    # menambahkan item yang baru ke dalam database
    data_item.append([id_item, nama_item, harga_item, stok_item])

    # menampilkan daftar item lengkap dengan item baru yang ditambahkan
    print("Item baru berhasil ditambahkan! Berikut daftar item yang terbaru:")
    show_item()


def read():
    # menampilkan seluruh item yang terdapat dalam database
    show_item()


def update():
    # input id item yang ingin diperbarui
    id_item = int(input("Masukkan ID item yang ingin di-update data: "))
    for i in range(len(data_item)):
        if data_item[i][0] == id_item:
            # input data item yang baru
            nama_item = input("Masukkan nama item baru: ")
            harga_item = int(input("Masukkan harga item baru: "))
            stok_item = int(input("Masukkan stok item baru: "))

            # melakukan update item yang dipilih
            data_item[i][1] = nama_item
            data_item[i][2] = harga_item
            data_item[i][3] = stok_item

            # menampilkan daftar item yang terbaru
            print("Data item berhasil di-update! Berikut daftar item yang terbaru:")
            show_item()
            break
    else:
        print("Item tidak ditemukan")


def delete():
    # input id item yang ingin dihapus
    id_item = int(input("Masukkan ID item yang ingin dihapus: "))
    for i in range(len(data_item)):
        if data_item[i][0] == id_item:
            # menghapus item sesuai input id
            data_item.pop(i)

            # menampilkan daftar item yang terbaru
            print("Data item berhasil dihapus! Berikut daftar item yang terbaru:")
            show_item()
            break
    else:
        print("Item tidak ditemukan")


# menampilkan seluruh item yang terdapat dalam database dengan prettytable
def show_item():
    table = PrettyTable()
    table.field_names = ["ID", "Nama Item", "Harga", "Stok"]
    for item in data_item:
        table.add_row(item)
    print(table)


# program utama
while True:

    print("-"*20)
    print("Toko Bibit Tanaman")
    print("-"*20)
    print("1. Admin")
    print("2. Pembeli")
    print("3. Keluar")

    choice = input("Pilih menu: ")


    print("-"*20)
    print("toko bibit tanaman")
    print("-"*20)
    print("1. LOGIN")
    print("2. EXIT")

    #login admin 
    
    menu_login = input("Silahkan Pilih Menu Dibawah ini :")
    if menu_login == "1" :
        username = input("Masukkan Username Anda  : ")
        password = input("Masukkan Password Anda  : ")

    if not password.isdigit() :
        print("password harus berupa angka")   

    if username == "admin ganteng" :
        password == "202005"



    #program admin

    if choice == "1":
        print("-"*20)
        print("Admin Toko Bibit Tanaman")
        print("-"*20)
        print("1. Tambah Item")
        print("2. Lihat Item")
        print("3. Update Item")
        print("4. Hapus Item")
        print("5. Kembali")

        admin_choice = input("Pilih menu: ")
        if admin_choice == "1":
            create()
        elif admin_choice == "2":
            read()
        elif admin_choice == "3":
            update()
        elif admin_choice == "4":
            delete()
        elif admin_choice == "5":
            continue
        else:
            print("Menu tidak tersedia")

    # program pembeli

    elif choice == "2":
        print("-"*20)
        print("Pembeli")
        print("-"*20)
        transaksi()
    elif choice == "3":
        print("Terima kasih telah menggunakan aplikasi ini.")
        break
    else:
        print("Menu tidak tersedia")





        

Pemrograman Berorientasi Objek (OOP) dalam Dart sangat bermanfaat dalam pengembangan aplikasi e-commerce karena memungkinkan pembuatan kode yang terstruktur, terorganisir, dan mudah dikelola. Berikut adalah beberapa penggunaan prinsip OOP dalam konteks aplikasi e-commerce:

### Penggunaan OOP dalam Pengembangan E-commerce

1. **Model Produk**
    - Membuat kelas untuk mewakili produk dengan atribut seperti id, nama, harga, deskripsi, dan stok.

2. **Keranjang Belanja (Shopping Cart)**
    - Membuat kelas untuk keranjang belanja yang dapat menambah, menghapus, dan menghitung total item.

3. **Pengguna dan Profil Pengguna**
    - Membuat kelas untuk pengguna yang menyimpan data seperti nama, alamat, dan riwayat pembelian.

4. **Transaksi dan Order**
    - Membuat kelas untuk menangani informasi order termasuk item yang dibeli, total harga, dan status pembayaran.

5. **Katalog Produk**
    - Mengelola koleksi produk menggunakan kelas yang memiliki metode untuk menyaring dan mencari produk.

6. **Manajemen Kupon dan Diskon**
    - Membuat kelas untuk mewakili kupon yang memiliki atribut seperti kode, jenis diskon, dan masa berlaku.

7. **Sistem Inventaris**
    - Mengelola stok produk dan memperbarui jumlah stok setelah penjualan.

8. **Interaksi API**
    - Kelas untuk berinteraksi dengan API eksternal guna mengambil atau mengirim data terkait produk, order, atau pengguna.

### Contoh Kode Dart Menggunakan OOP

#### Model Produk
```dart
class Product {
  String id;
  String name;
  double price;
  String description;
  int stock;

  Product({required this.id, required this.name, required this.price, required this.description, required this.stock});

  void updateStock(int newStock) {
    stock = newStock;
  }

  @override
  String toString() {
    return 'Product{id: $id, name: $name, price: $price, description: $description, stock: $stock}';
  }
}

void main() {
  Product product = Product(id: 'P001', name: 'Smartphone XYZ', price: 299.99, description: 'A high-quality smartphone with advanced features.', stock: 150);
  print(product);

  // Update stock
  product.updateStock(120);
  print('Updated product: $product');
}
```

#### Keranjang Belanja
```dart
class CartItem {
  String productId;
  int quantity;

  CartItem({required this.productId, required this.quantity});
}

class ShoppingCart {
  List<CartItem> items = [];

  void addItem(String productId, int quantity) {
    items.add(CartItem(productId: productId, quantity: quantity));
  }

  void removeItem(String productId) {
    items.removeWhere((item) => item.productId == productId);
  }

  double calculateTotal(Map<String, double> productPrices) {
    double total = 0.0;
    for (var item in items) {
      total += (productPrices[item.productId]! * item.quantity);
    }
    return total;
  }

  @override
  String toString() {
    return 'ShoppingCart{items: $items}';
  }
}

void main() {
  ShoppingCart cart = ShoppingCart();
  cart.addItem('P001', 2);
  cart.addItem('P002', 1);
  print(cart);

  // Calculate total price
  Map<String, double> productPrices = {'P001': 299.99, 'P002': 499.99};
  double totalPrice = cart.calculateTotal(productPrices);
  print('Total Price: \$${totalPrice}');
}
```

#### Pengguna dan Profil Pengguna
```dart
class UserProfile {
  String userId;
  String name;
  String address;
  List<String> purchaseHistory;

  UserProfile({required this.userId, required this.name, required this.address, required this.purchaseHistory});

  void addPurchase(String orderId) {
    purchaseHistory.add(orderId);
  }

  @override
  String toString() {
    return 'UserProfile{userId: $userId, name: $name, address: $address, purchaseHistory: $purchaseHistory}';
  }
}

void main() {
  UserProfile user = UserProfile(userId: 'U001', name: 'John Doe', address: '123 Elm Street', purchaseHistory: []);
  print(user);

  // Add a purchase
  user.addPurchase('O12345');
  print('Updated user profile: $user');
}
```

#### Order Management
```dart
class Order {
  String orderId;
  List<CartItem> items;
  double totalAmount;
  String status;

  Order({required this.orderId, required this.items, required this.totalAmount, required this.status});

  void updateStatus(String newStatus) {
    status = newStatus;
  }

  @override
  String toString() {
    return 'Order{orderId: $orderId, items: $items, totalAmount: $totalAmount, status: $status}';
  }
}

void main() {
  List<CartItem> items = [CartItem(productId: 'P001', quantity: 2), CartItem(productId: 'P002', quantity: 1)];
  Order order = Order(orderId: 'O12345', items: items, totalAmount: 899.97, status: 'Pending');
  print(order);

  // Update order status
  order.updateStatus('Shipped');
  print('Updated order: $order');
}
```

Dengan menggunakan OOP, Anda dapat membuat struktur kode yang modular dan mudah di-maintain, memudahkan pengembangan dan pemeliharaan fitur-fitur kompleks dalam aplikasi e-commerce.
# API Endpoints Documentation
## Marketplace with Escrow System

---

## 1. Authentication & User Management

### Authentication
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/auth/register` | Register user baru |
| `POST` | `/api/auth/login` | Login user |
| `POST` | `/api/auth/refresh` | Refresh access token |
| `POST` | `/api/auth/logout` | Logout (hapus refresh token) |
| `POST` | `/api/auth/forgot-password` | Request reset password |
| `POST` | `/api/auth/reset-password` | Reset password dengan token |

### User Profile Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/auth/me` | Get current user info |
| `PUT` | `/api/auth/me` | Update basic user info |
| `PUT` | `/api/auth/me/password` | Change password |
| `PUT` | `/api/auth/me/profile` | Update profile lengkap |
| `PUT` | `/api/auth/me/bank` | Update bank info |
| `POST` | `/api/auth/me/seller/activate` | Activate seller mode |
| `PUT` | `/api/auth/me/seller/profile` | Update seller profile |

---

## 2. Products & Marketplace

### Browse Products (Public)
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/products` | List semua produk aktif |
| `GET` | `/api/products/search` | Search produk |
| `GET` | `/api/products/categories` | Get kategori produk |
| `GET` | `/api/products/latest` | Produk terbaru |
| `GET` | `/api/products/popular` | Produk populer |
| `GET` | `/api/products/{id}` | Detail produk |

### Seller Product Management (Protected)
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/seller/products` | List produk seller |
| `POST` | `/api/seller/products` | Create produk baru |
| `GET` | `/api/seller/products/{id}` | Detail produk seller |
| `PUT` | `/api/seller/products/{id}` | Update produk |
| `DELETE` | `/api/seller/products/{id}` | Soft delete produk |
| `PUT` | `/api/seller/products/{id}/status` | Update status produk |

### Product Images
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/seller/products/{id}/images` | Upload gambar produk |
| `DELETE` | `/api/seller/products/{id}/images/{imageId}` | Hapus gambar |
| `PUT` | `/api/seller/products/{id}/images/{imageId}/cover` | Set cover image |

---

## 3. Order & Checkout Process

### Cart & Checkout
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/orders/checkout` | Create order + transaction |
| `GET` | `/api/orders/checkout/{orderId}` | Get checkout info |

### Order Management - Buyer
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/orders` | List orders sebagai buyer |
| `GET` | `/api/orders/{id}` | Detail order |
| `POST` | `/api/orders/{id}/cancel` | Cancel order (jika pending) |
| `POST` | `/api/orders/{id}/confirm` | Confirm order received |

### Order Management - Seller
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/seller/orders` | List orders sebagai seller |
| `GET` | `/api/seller/orders/{id}` | Detail order seller |
| `POST` | `/api/seller/orders/{id}/accept` | Accept order |
| `POST` | `/api/seller/orders/{id}/reject` | Reject order |
| `POST` | `/api/seller/orders/{id}/process` | Start processing |
| `POST` | `/api/seller/orders/{id}/ship` | Ship order (with tracking) |
| `POST` | `/api/seller/orders/{id}/complete` | Mark as completed |

---

## 4. Payment & Transactions

### Payment Gateway Integration
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/payments/create` | Create payment link |
| `POST` | `/api/payments/webhook` | Payment gateway webhook |
| `GET` | `/api/payments/{orderId}/status` | Check payment status |

### Transaction History
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/transactions` | User transaction history |
| `GET` | `/api/transactions/{id}` | Detail transaksi |

---

## 5. Escrow & Balance Management

### Balance & Earnings (Seller)
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/seller/balance` | Get current balance |
| `GET` | `/api/seller/earnings` | Earnings history/report |

### Withdrawal System
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/withdrawals/request` | Request penarikan dana |
| `GET` | `/api/withdrawals` | List withdrawal requests |
| `GET` | `/api/withdrawals/{id}` | Detail withdrawal |
| `POST` | `/api/withdrawals/{id}/cancel` | Cancel withdrawal (if pending) |

---

## 6. Chat & Communication

### Chat System
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/chats` | List chats user |
| `GET` | `/api/chats/{orderId}` | Get/create chat untuk order |
| `GET` | `/api/chats/{chatId}/messages` | Get messages |
| `POST` | `/api/chats/{chatId}/messages` | Send message |
| `PUT` | `/api/chats/{chatId}/read` | Mark messages as read |

---

## 7. Admin Panel (ADMIN ONLY)

### Dashboard & Stats
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/dashboard` | Admin dashboard stats |

### User Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/users` | List all users |
| `GET` | `/api/admin/users/{id}` | User detail |
| `PUT` | `/api/admin/users/{id}/status` | Activate/deactivate user |
| `DELETE` | `/api/admin/users/{id}` | Delete user |

### Product Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/products` | List all products |
| `PUT` | `/api/admin/products/{id}/status` | Approve/reject product |
| `DELETE` | `/api/admin/products/{id}` | Delete product |

### Order Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/orders` | List all orders |
| `GET` | `/api/admin/orders/{id}` | Order detail |
| `POST` | `/api/admin/orders/{id}/dispute` | Handle dispute |

### Transaction Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/transactions` | All transactions |
| `GET` | `/api/admin/transactions/stats` | Transaction statistics |

### Withdrawal Management
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/withdrawals` | All withdrawal requests |
| `POST` | `/api/admin/withdrawals/{id}/approve` | Approve withdrawal |
| `POST` | `/api/admin/withdrawals/{id}/reject` | Reject withdrawal |

### Reports
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/admin/reports/sales` | Sales report |
| `GET` | `/api/admin/reports/users` | User activity report |
| `GET` | `/api/admin/reports/revenue` | Revenue report |

---

## 8. Utilities & Helpers

### File Upload
| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/upload/image` | Upload single image |
| `POST` | `/api/upload/images` | Upload multiple images |

### Notifications
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/notifications` | User notifications |
| `PUT` | `/api/notifications/{id}/read` | Mark notification as read |
| `PUT` | `/api/notifications/read-all` | Mark all as read |

### System Info
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/system/status` | System health check |
| `GET` | `/api/system/categories` | Available categories |
| `GET` | `/api/system/fees` | Platform fees info |

---

## Application Flow

### 1. Onboarding Flow
1. `POST /api/auth/register` - Register user baru
2. `POST /api/auth/login` - Login user
3. `PUT /api/auth/me/profile` - Complete profile

### 2. Buyer Flow
1. `GET /api/products` - Browse products
2. `POST /api/orders/checkout` - Create order
3. `POST /api/payments/create` - Process payment
4. `GET /api/chats/{orderId}` - Communicate with seller
5. `POST /api/orders/{id}/confirm` - Confirm order received

### 3. Seller Flow
1. `POST /api/auth/me/seller/activate` - Activate seller mode
2. `POST /api/seller/products` - Add products
3. `GET /api/seller/orders` - Manage incoming orders
4. `POST /api/seller/orders/{id}/ship` - Ship orders
5. `POST /api/withdrawals/request` - Request withdrawal

### 4. Admin Flow
1. `GET /api/admin/dashboard` - Monitor platform
2. `GET /api/admin/withdrawals` - Review withdrawal requests
3. `POST /api/admin/withdrawals/{id}/approve` - Approve withdrawals

---

## Authentication & Authorization

- **Public endpoints**: Product browsing, system info
- **User endpoints**: Require valid JWT token
- **Seller endpoints**: Require seller activation
- **Admin endpoints**: Require admin role
- **Webhook endpoints**: Require signature validation
# Cimri Market API

Cimri.com market ürünlerini programatik olarak aramak, fiyatları karşılaştırmak ve en uygun fiyatları bulmak için geliştirilmiş bir API.

## Kurulum

1. Projeyi klonlayın
2. PHP 7.4 veya üzeri sürüm gereklidir
3. PHP'nin curl ve json eklentileri aktif olmalıdır
4. Web sunucusunu başlatın:
```bash
php -S localhost:8000
```

## Kullanım

### Ürün Arama
```
GET /api.php?q=seker
GET /api.php?q=seker&sort=price-asc
GET /api.php?q=seker&page=2
```

### Ürün Detayları
```
GET /product.php?path=torku-toz-seker-1-kg-p-123456
```

### Resim ve Logo
```
GET /image.php?file=urun-resmi.jpg&size=md
GET /logo.php?id=12345
```

## Önbellek Yönetimi

- Önbellek dosyaları `cache/` dizininde saklanır
- Her dosya için benzersiz MD5 hash kullanılır
- Maksimum 500 dosya sınırı vardır
- Otomatik temizleme:
  - Uygulama başlatıldığında
  - Yeni cache yazılırken
  - Limit aşıldığında
  - Süresi geçmiş dosyalar için

## Güvenlik Önlemleri

1. Rate Limiting
   - Rastgele bekleme süreleri
   - Akıllı retry mekanizması
   - Rate limit aşımında uzun bekleme

2. User Agent Rotasyonu
   - Gerçekçi tarayıcı bilgileri
   - Her istek için farklı user agent
   - Tarayıcıya uygun headerlar

3. Hata Yönetimi
   - Detaylı loglama
   - Otomatik retry
   - Timeout kontrolü

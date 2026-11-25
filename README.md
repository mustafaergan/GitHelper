# GitHelper

Git ile sık gereken ama akılda kalmayan komutlar için kısa notlar.

> **Not:** Bu depo 2024 yılında kişisel not olarak oluşturuldu ve artık güncellenmiyor.

## Branch ezme

Bir dalın (hedef) içeriğini, geçmişini silmeden başka bir dalın (kaynak) içeriğiyle tamamen değiştirmek için
`ours` birleştirme stratejisi kullanılır. Zorla gönderme (`push --force`) gerekmez; hedef dalın geçmişi korunur.

```bash
git checkout KAYNAK          # içeriği korunacak dal
git merge -s ours HEDEF      # HEDEF'i birleştirilmiş say, ama KAYNAK'ın içeriğini koru
git checkout HEDEF
git merge KAYNAK             # HEDEF artık KAYNAK'ın içeriğine sahip (fast-forward)
```

Örnek: `R2/MASTER` dalını `R2/MASTER_REVERT` dalının içeriğiyle ezmek için

```bash
git checkout R2/MASTER_REVERT
git merge -s ours R2/MASTER
git checkout R2/MASTER
git merge R2/MASTER_REVERT
```

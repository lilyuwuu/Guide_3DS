# F3 (Linux)

## Required Reading

Bu, SD kartınızı F3 kullanarak hatalar olup olmadığını kontrol etmek için kullanılan bir eklenti bölümdür.

SD kartınızın boyutuna ve bilgisayarınıza bağlı olarak bu işlem bir kaç saat sürebilir!

Bu sayfa yalnızca Linux kullanıcıları içindir. If you are not on Linux, check out the [H2testw (Windows)](h2testw-\(windows\)) or [F3XSwift (Mac)](f3xswift-\(mac\)) pages.

## What You Need

- The latest version of [F3](https://github.com/AltraMayor/f3/releases/tag/v8.0)

## Instructions

1. f3 `.zip` dosyasını zipten çıkarın
2. f3 dizinine 'cd' ile gidin
3. F3'ü derlemek için `make` çalıştırın
4. SD kartınızı bilgisayarınıza takın
5. SD kartınızı mount edin
6. Çalıştır `./f3read <your sd card mount point>`
7. İşlem tamamlanana kadar bekleyin. Örnek çıktı için aşağıya bakın.

```bash
$ ./f3write /media/michel/6135-3363/
Free space: 29.71 GB
Creating file 1.h2w ... OK!
...
Creating file 30.h2w ... OK!
Free space: 0.00 Byte
Average Writing speed: 4.90 MB/s
```

1. Çalıştır `./f3read <your sd card mount point>`
2. İşlem tamamlanana kadar bekleyin. Örnek çıktı için aşağıya bakın.

```bash
$ ./f3read /media/michel/6135-3363/
									SECTORS      ok/corrupted/changed/overwritten
Validating file 1.h2w ... 2097152/        0/      0/      0
...
Validating file 30.h2w ... 1491904/        0/      0/      0

	Data OK: 29.71 GB (62309312 sectors)
Data LOST: 0.00 Byte (0 sectors)
					Corrupted: 0.00 Byte (0 sectors)
	Slightly changed: 0.00 Byte (0 sectors)
				Overwritten: 0.00 Byte (0 sectors)
Average Reading speed: 9.42 MB/s
```

___

::: tip

If the test shows the result `Data LOST: 0.00 Byte (0 sectors)`, your SD card is good and you can delete all `.h2w` files on your SD card.

:::

::: danger

Test diğer sonuçları gösteriyorsa, SD kartınız bozuk veya hasar görmüş olabilir ve değiştirmeniz gerekebilir!

:::

::: tip

Return to [Get Started](get-started)

:::

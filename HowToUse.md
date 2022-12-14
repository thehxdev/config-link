# آموزش استفاده از برنامه

**قبل از هرچیزی توجه کنید که این آموزش برای سرور های `Ubuntu` و `Debian` هست.**

- در قسمت هایی که بصورت کد قرار گرفتن علامت `#` یعنی اون قسمت دستور نیست.

### نصب پکیج های مورد نیاز

با دستور پایین پکیج‌های مورد نیاز رو نصب کنید:

```bash
apt install micro vim git curl wget unzip 
```

### مراحل استفاده از برنامه

1. با دستور زیر این ریپازیتوری رو Clone کنید:

```bash
git clone --depth 1 https://github.com/thehxdev/config-link /root/config-link
```

2. به دایرکتوری ایجاد شده میرید و با استفاده از ادیتور `micro` کانفیگ سرور خودتون رو به فایل های `clash.yaml` و `surfboard.conf` اضافه کنید.

```bash
cd /root/config-link/

# Clash
micro clash.yaml

# Surfboard
micro surfboard.conf

# Every V2ray/Xray client that supports subscription
micro xray.txt
```

3. بعد از اضافه کردن کانفیگ‌ها به فایل های مربوطه اون برنامه، میتونید از ادیتور `micro` با دکمه های `ctrl + q` خارج بشید. (با دکمه های `ctrl + s` هم فایل save میشه.)

4. حالا میتونید برنامه رو اجرا کنید تا روی پورت `3000` شروع به گوش دادن بکنه.
تا زمانی که برنامه اجرا شده باقی بمون میتونید با لینک های پایین کانفیگ هارو به برنامه مربوطه اضافه کنید.

اجرای برنامه:

```bash
./app
```

لینک ها:

```bash
# Clash
http://SERVER_IP:3000/clash.yaml

# Surfboard
http://SERVER_IP:3000/surfboard.conf

# V2ray/Xray
http://SERVER_IP:3000/xray.txt
```

اگر دامنه اینترنتی دارید که یک رکورد DNS از نوع A/AAAA هم براش ساختید که به سرور شما اشاره میکنه میتونید بجای IP سرور از دامنه استفاده کنید.

با زدن دکمه های `ctrl + c` هم میتونید برنامه رو ببندید تا دیگه لینک ها قابل استفاده نباشن. برای دوباره استفاده کردن هم خیلی ساده باید برنامه اجرا کنید.


## اجرای برنامه بصورت دائمی

برای اینکه لینک ها همیشه قابل استفاده باشن میتونید از فایل `conflink.service` استفاده کنید.

1. فایل `conflink.service` رو به دایرکتوری `systemd` کپی میکنیم و بعد سرویس ایجاد شده رو اجرا میکنیم.

```bash
cp /root/config-link/conflink.service /usr/lib/systemd/system/conflink.service

systemctl enable --now conflink.service
```

با دستور پایین چک کنید که برنامه روی پورت `3000` درحال اجرا باشه.

```bash
ss -tupln | grep 3000
```

با دستور آخر برنامه حتی بعد از خاموش روشن شدن (ریستارت) سرور هم اجرا میشه.

برای بستن برنامه و غیرقابل استفاده کردن لینک ها دستور پایین رو میزنید تا سرویس استاپ بشه:

```bash
systemctl disable --now conflink.service
```


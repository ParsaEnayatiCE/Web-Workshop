<div dir = "rtl">
<h1 dir = "rtl">
رندر کردن شرطی:
</h1>

<h2>
دستور <code>v-if</code>:
</h2>

دستور <code>v-if</code> برای رندر کردن یک بلوک به صورت مشروط استفاده می شود. بلوک تنها در صورتی ارائه می شود که عبارت دستور یک مقدار واقعی را برگرداند.

```vue
<h1 v-if="awesome">Vue is awesome!</h1>
```
<h2>
دستور <code>v-else</code>:
</h2>

می‌توانید از دستور <code>v-else</code> برای نشان دادن یک بلوک <code>else</code> برای <code>v-if</code> استفاده کنید:

```vue
<button @click="awesome = !awesome">Toggle</button>
```
```vue
<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
```
<h2>
دستور <code>v-else-if</code>:
</h2>
<code>v-else-if</code>، همانطور که از نام آن پیداست، به عنوان یک شرط جدید در صورت نقض شرط برای v-if عمل می کند. همچنین می توان آن را چندین بار زنجیر کرد:

```vue
<template>
    <div v-if="type === 'A'">
      A
    </div>
    <div v-else-if="type === 'B'">
      B
    </div>
    <div v-else-if="type === 'C'">
      C
    </div>
    <div v-else>
      Not A/B/C
    </div>
</template>
```
<h2>
دستور v-show:
</h2>
گزینه دیگر برای نمایش شرطی یک عنصر دستور v-show است. کاربرد تا حد زیادی یکسان است:

```vue
<h1 v-show="ok">Hello!</h1>
```

تفاوت این است که یک عنصر با 
<code>v-show</code>
همیشه رندر می شود و در DOM باقی می ماند. <code>v-show</code> فقط ویژگی نمایش CSS عنصر را تغییر می دهد.

<h3>
مقایسه v-if  با v-show :
</h3>
<code>v-if</code> رندر شرطی «واقعی» است زیرا تضمین می‌کند که لیسنرهای رویداد و مؤلفه‌های فرزند در داخل بلوک شرطی به درستی از بین رفته و در حین جابجایی دوباره ایجاد می‌شوند. <code>v-if</code> نیز به صورت lazy است: اگر شرط در رندر اولیه false باشد، کاری انجام نمی دهد - بلوک شرطی تا زمانی که شرط برای اولین بار درست نشود، رندر نمی شود. در مقایسه، <code>v-show</code> بسیار ساده‌تر است - عنصر همیشه بدون در نظر گرفتن شرایط اولیه، با جابجایی مبتنی بر CSS ارائه می‌شود. به طور کلی، <code>v-if</code> دارای هزینه های تعویض بالاتر است در حالی که <code>v-show</code> هزینه های رندر اولیه بالاتری دارد. بنابراین اگر نیاز دارید چیزی را اغلب تغییر دهید <code>v-show</code> را ترجیح دهید و اگر بعید است که شرایط در زمان اجرا تغییر کند، <code>v-if</code> را ترجیح دهید.

</div>

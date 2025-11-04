# TypeScript’e Giriş

> Herkese merhaba! TypeScript ders serimizin ilk videosuna hoş geldiniz.
>
> Bu içerikte “TypeScript nedir?”, “Neden kullanılır?” ve “JavaScript’ten farkı ne?” sorularına yanıt vereceğiz.
>
> Eğer siz de JavaScript yazarken beklenmedik hatalarla karşılaşıyorsanız, TypeScript tam size göre. Hadi başlayalım!

![TypeScript Intro – JavaScript + Type Safety = TypeScript](/ts-hero.svg)

---

## TypeScript Nedir?

TypeScript, Microsoft tarafından geliştirilen açık kaynaklı bir programlama dilidir. Aslında JavaScript’in bir üst versiyonu (superset) diyebiliriz. TypeScript, JavaScript’in tüm özelliklerini içerir ama buna ek olarak **tip güvenliği** (type safety) sağlar.

Yani değişkenlerinizin hangi türde olduğunu belirleyebilir ve bu türü yanlış kullandığınızda, daha kodu çalıştırmadan hata alabilirsiniz.

Örneğin, JavaScript’te şöyle bir kod yazabiliriz:

```js
let age = 25;
age = "yirmi beş"; // hata vermez
```

Ama TypeScript’te aynı şeyi yazarsak, kodu derlemeden önce hata verir:

```ts
let age: number = 25;
age = "yirmi beş"; // hata! string number olamaz
```

![Yan yana JS (sorunsuz) ve TS (tip hatası) karşılaştırması](/ts-compare.svg)

---

## Neden TypeScript Kullanmalıyız?

Büyük projelerde JavaScript kodları hızla karmaşık hale gelir. Bir değişkenin, bir fonksiyonun veya bir nesnenin hangi türde olduğunu hatırlamak zorlaşır. TypeScript bu noktada devreye girer ve sizin için bu bilgileri saklar.

- Hataları erkenden yakalar (derleme zamanında)
- Geliştirme sürecini hızlandırır (otomatik tamamlama, tip ipuçları)
- Kodu daha **güvenli** ve **okunabilir** hale getirir

Ayrıca TypeScript ile yazdığınız kod, **derleme** aşamasında JavaScript’e dönüştürülür. Yani TypeScript yazarsınız ama tarayıcıda yine JavaScript çalışır.

![TS kodu → JS’e dönüştürülür → Tarayıcıda çalışır diyagramı](/ts-pipeline.svg)

---

## TypeScript Nerelerde Kullanılır?

- **Frontend (React, Next.js):** Bileşen prop’larının ve state’in net tiplenmesi, autocomplete ve güvenli refactor sağlar. Büyük UI kod tabanlarında hataları derlemede yakalar.
- **Backend (Node.js, Express/NestJS):** API istek/yanıt şemalarını ve servis katmanlarını kesin tiplerle tanımlayarak veri uyumsuzluklarını azaltır.
- **Full‑stack paylaşılan tipler:** `@types` paketleri veya ortak bir `types` klasörüyle hem client hem server aynı tipleri kullanır; uçtan uca güvenli sözleşmeler.
- **Kütüphane/SDK geliştirme:** Public API’ler için zengin tür açıklamaları, kullanıcı IDE’lerinde güçlü dokümantasyon sunar.
- **CLI ve araçlar:** Node tabanlı komut satırı araçlarında güvenli argüman ve config tipleri.
- **Monorepo (Turborepo/Nx):** Paketler arası tip paylaşımı, derleme performansı ve ölçeklenebilir yapılandırmalar.

### Ne Zaman TS Tercih Etmeli?

- Ekip ve kod tabanı büyüyorsa, sık refactor yapılıyorsa, domain karmaşıksa.
- Dış servislerle (API, veritabanı) yoğun veri alışverişi yapılıyorsa.
- Uzun ömürlü projelerde bakım maliyetini düşürmek isteniyorsa.

Küçük script’lerde saf JS yeterli olabilir; ancak proje büyüdükçe TS’nin sağladığı erken hata tespiti ve güçlü araç desteği toplam maliyeti düşürür.

## Kurulum ve İlk Örnek

İlk olarak bilgisayarınızda Node.js kurulu olmalı. Ardından terminalde:

```bash
npm install -g typescript
```

Kurulumu doğrulamak için:

```bash
tsc --version
```

Ardından masaüstünüzde bir klasör açın ve içinde `hello.ts` oluşturun:

```ts
let message: string = "Merhaba TypeScript!";
console.log(message);
```

Derleyelim:

```bash
tsc hello.ts
```

Aynı klasörde `hello.js` oluşur. Çalıştırın:

```bash
node hello.js
```

Ekranda “Merhaba TypeScript!” çıktıysa, kurulum tamam! 🎉

![VS Code + Terminal: tsc derleme ve çıktı](/ts-pipeline.svg)

---

## Kısa Örnekler: Tip Tanımlama, Fonksiyonlar, Arayüzler

### Tip Tanımlama
```ts
let ad: string = "Ayberk";
let yas: number = 25;
let aktif: boolean = true;
```

### Fonksiyon Tipleri
```ts
function topla(a: number, b: number): number {
  return a + b;
}

console.log(topla(3, 7));
```

### Nesneler ve Arayüzler (Interfaces)
```ts
interface Kullanici {
  isim: string;
  yas: number;
}

let user: Kullanici = { isim: "Ayberk", yas: 25 };
```

![Tip ipuçları (string, number) baloncukları konsepti](/ts-hints.svg)

---

## Sonuç ve Sıradaki İçerikler

Bugün TypeScript’in ne olduğunu, neden kullanıldığını ve nasıl kurulduğunu gördük. Bir sonraki derste TypeScript’in **değişken türleri**, **fonksiyon yapıları** ve **class’lar** konusuna geçeceğiz.

Beğendiyseniz serinin devamı için destek olmayı unutmayın. Bir sonraki içerikte görüşmek üzere! 👋

> Sıradaki: TypeScript Temelleri — Değişkenler, Fonksiyonlar, Class’lar


---

## Ek: Gelişmiş TypeScript Konuları (Derinlemesine)

### Tür Çıkarımı (Type Inference)
TypeScript, çoğu durumda türleri otomatik çıkarır. Gereksiz anotasyonlar yerine çıkarımdan yararlanmak okunabilirliği artırır.

```ts
const count = 0;           // number
let title = "EmaDocs";    // string
const flags = [true, false]; // boolean[]

// İpucu: const ile literal türler korunur
const STATUS = { OK: "ok", ERR: "err" } as const;
// typeof STATUS.OK ⇒ "ok"
```

### Strict Modlar (tsconfig)
Önerilen ayarlar:

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "exactOptionalPropertyTypes": true,
    "noUncheckedIndexedAccess": true
  }
}
```

Bu bayraklar, null/undefined kaynaklı hataları ve eksik alanları derleme sırasında yakalamanıza yardımcı olur.

### Yapısal Türleme ve Uyumluluk
TypeScript yapısal tipler kullanır: şekil aynıysa uyumludur.

```ts
type Point = { x: number; y: number };
type Pixel = { x: number; y: number; color?: string };

const p: Point = { x: 1, y: 2 };
const q: Pixel = p; // uyumlu (fazlalık alan zorunlu değil)
```

### Tür Daraltma (Narrowing)
`typeof`, `in`, `instanceof` ve kullanıcı tanımlı koruyucularla kesinleşen kollar yazın.

```ts
function isString(v: unknown): v is string {
  return typeof v === "string";
}

function len(v: string | string[]) {
  if (isString(v)) return v.length;   // string
  return v.join(",").length;        // string[]
}
```

### Generics (Kısıtlar, Varsayılanlar)

```ts
function wrap<T>(value: T): { value: T } { return { value }; }

// Kısıtlı generic
function getId<T extends { id: string }>(x: T) { return x.id; }

// Varsayılan tür parametresi
type ApiResponse<T = unknown> = { ok: true; data: T } | { ok: false; error: string };
```

### Keyof, Indexed Access, Mapped Types

```ts
type Keys<T> = keyof T;      // anahtar kümeleri
type Value<T, K extends keyof T> = T[K]; // alan tipi

type ReadonlyDeep<T> = { readonly [K in keyof T]: ReadonlyDeep<T[K]> };
```

### Koşullu Türler ve Dağıtım

```ts
type Awaited<T> = T extends Promise<infer U> ? Awaited<U> : T;

type ExcludeNull<T> = T extends null | undefined ? never : T;
```

### Yerleşik Utility Türleri
- `Partial<T>`, `Required<T>`, `Readonly<T>`
- `Pick<T, K>`, `Omit<T, K>`
- `Record<K, V>`
- `ReturnType<F>`, `Parameters<F>`

Uygulamada API şemaları ve form tiplerinde çok faydalıdır.

### Deklarasyon Dosyaları ve DefinitelyTyped
Türü olmayan kütüphaneler için `@types/*` paketlerini kullanın. Gerekirse minimal `declarations.d.ts` ile eksikleri tanımlayın.

### Modüller ve Tür Paylaşımı
Full‑stack projelerde ortak tipleri `@/types` gibi bir pakette toplayıp hem server hem client tarafında kullanın. Sürümlemede kopmaları önlemek için CI’da tür denetimi çalıştırın.

### Geçiş Stratejisi (JS → TS)
1. tsconfig ekleyin, `allowJs: true` ile başlayın.
2. Kritik modülleri `.ts/.tsx`’e dönüştürün.
3. `any` geçicidir; zamanla `unknown` + daraltma ve doğru modelleme ile temizleyin.
4. Son aşamada `noImplicitAny` ve diğer strict bayrakları açın.

### En İyi Pratikler
- Türleri iş kurallarının diline göre isimlendirin; domain modelini yansıtın.
- Fazla genel `any` yerine `unknown` + daraltma kullanın.
- API sözleşmeleri için türleri tek kaynakta (shared) tutun.
- Fazla karmaşık türleri basitleştirin; gerektiğinde küçük ara tipler tanımlayın.
- Lint kuralları ve `tsc --noEmit` ile tür hatalarını CI’da bloklayın.

### Yaygın Tuzaklar
- Fazla `as` kullanımı: yanlış güvenlik hissi yaratır.
- `Date`, `JSON`, `Map/Set` gibi yerleşiklerin tiplerini ve çalışma zamanı kısıtlarını karıştırmak.
- `enum` yerine çoğu senaryoda union‑literal kullanmak daha güvenlidir.

### Testlerde Tür Güvenliği
Jest/Vitest ile tip kontrollerini ayırın: `tsc -p tsconfig.json --noEmit` CI adımı, testlerden bağımsız olarak tür hatalarını yakalar.



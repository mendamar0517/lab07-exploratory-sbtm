# BUG-11: Footer-ийн «Хуучин хувилбар» линк (/old) 500 Internal Server Error буцаадаг

Орчин:  Уншлагын жагсаалт v2.0, Chromium 153.0.8010.12, Linux x86_64 (Node.js v22.23.4), 2026-10-24

Урьдчилсан нөхцөл: node app.js-ийг шинээр асаасан (анхны 3 ном), браузерт http://localhost:3000 нээсэн

## Дахин гаргах алхам

1. Хуудасны доод талын «Хуучин хувилбар» линкийг дарна.
2. (API) `curl -i localhost:3000/old`

Хүлээгдэж байсан: Спец: «бүх хуудас, линк ажиллана.»

Бодит үр дүн:     /old хуудсанд зөвхөн «Internal Server Error» бичвэр гарна; curl -i -> `HTTP/1.1 500 Internal Server Error`.

Ноцтой байдал: Major — UI-д харагдах линк серверийн алдаа үүсгэнэ.

Хавсралт:      ![BUG-11](../screenshots/bug-11.png) · [evidence/bug-11-curl.txt](../evidence/bug-11-curl.txt)

Олдсон аялал:  Supermodel, Saboteur

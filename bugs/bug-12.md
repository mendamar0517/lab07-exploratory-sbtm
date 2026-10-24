# BUG-12: API: буруу JSON биетэй POST /api/books хүсэлтэд 400 биш 200 OK {"result":"OK"} буцаадаг

Орчин:  Уншлагын жагсаалт v2.0, Chromium 153.0.8010.12, Linux x86_64 (Node.js v22.23.4), 2026-10-24

Урьдчилсан нөхцөл: node app.js-ийг шинээр асаасан (анхны 3 ном), браузерт http://localhost:3000 нээсэн

## Дахин гаргах алхам

1. Терминалд: `curl -i -X POST localhost:3000/api/books -d 'буруу оролт' 2>&1 | tee evidence/bug-12-curl.txt`
2. Мөн: `curl -i -X POST localhost:3000/api/books -H 'Content-Type: application/json' -d '{"title":'`
3. `curl -i localhost:3000/api/books` -> номын тоог харна.

Хүлээгдэж байсан: Спец: «API: буруу JSON биетэй POST хүсэлтэд 400 алдаа буцаана.»

Бодит үр дүн:     Хоёр хүсэлт хоёулаа `HTTP/1.1 200 OK`, бие `{"result":"OK"}`. Ном нэмэгдээгүй (GET /api/books 3 ном хэвээр) — сервер алдааг чимээгүй залгиж, клиентэд амжилт гэж худал мэдээлнэ.

Ноцтой байдал: Major — API-ийн гэрээ зөрчигдөж, клиент алдааг илрүүлэх боломжгүй.

Хавсралт:      [evidence/bug-12-curl.txt](../evidence/bug-12-curl.txt) · [evidence/bug-12-curl-json.txt](../evidence/bug-12-curl-json.txt)

Олдсон аялал:  Saboteur

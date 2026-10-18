# BUG-01: Буруу JSON хүсэлтэд HTTP 200 OK буцааж байна

- **Status:** Confirmed
- **Test result:** FAIL
- **Type:** API / Data validation
- **Severity:** Major

## Environment
- Application: http://localhost:3000/
- Endpoint: POST /api/books
- Content-Type: application/json

## Preconditions
Application ажиллаж байгаа бөгөөд API endpoint-д хандах боломжтой.

## Steps to Reproduce
1. Terminal нээнэ.
2. Дараах хүсэлтийг илгээнэ:

   ```bash
   curl -i -X POST 'http://localhost:3000/api/books' 
     -H 'Content-Type: application/json' 
     --data-binary '{"title":'
   ```

3. HTTP status болон response body-г шалгана.

## Expected Result
Буруу форматтай JSON хүсэлтийг сервер татгалзаж, 4xx төрлийн алдаа буцаана.

## Actual Result
Хадгалсан гаралтад `HTTP/1.1 200 OK` болон `{"result":"OK"}` гэж харагдсан.

## Evidence
[evidence/bug-api-01-curl.txt](../evidence/bug-api-01-curl.txt)

## Test Result
FAIL — буруу JSON хүсэлт амжилттай боловсруулагдсан мэт хариу авсан.

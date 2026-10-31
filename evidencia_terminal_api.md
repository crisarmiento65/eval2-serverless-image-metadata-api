# Evidencia de pruebas de la API - Terminal

## 1. POST /upload - Subida de imagen exitosa

```bash
csarmiento@cristobals:~/eval2-serverless/docs$ curl -s -X POST https://hakg55gysh.execute-api.us-east-1.amazonaws.com/dev/upload \
  -H "Content-Type: application/octet-stream" \
  -d @/tmp/imagen_b64.txt | python3 -m json.tool
{
    "message": "Image uploaded successfully!",
    "url": "https://my-image-storage-bucket-csarmiento-2026.s3.amazonaws.com/a2073ac806e546de94afe4eadeb2e95f.jpg"
}
```

## 2. GET /metadata/{id} - Consulta de metadatos exitosa

```bash
csarmiento@cristobals:~/eval2-serverless/docs$ curl -s -X GET https://hakg55gysh.execute-api.us-east-1.amazonaws.com/dev/metadata/a2073ac806e546de94afe4eadeb2e95f | python3 -m json.tool
{
    "url": "https://my-image-storage-bucket-csarmiento-2026.s3.amazonaws.com/a2073ac806e546de94afe4eadeb2e95f.jpg",
    "size": 376108.0,
    "image_id": "a2073ac806e546de94afe4eadeb2e95f"
}
```

## 3. GET /metadata/{id} - Imagen no encontrada (404)

```bash
csarmiento@cristobals:~/eval2-serverless/docs$ curl -s -X GET https://hakg55gysh.execute-api.us-east-1.amazonaws.com/dev/metadata/id-que-no-existe | python3 -m json.tool
{
    "message": "Image not found"
}
```

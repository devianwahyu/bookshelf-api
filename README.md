# Bookshelf API

### API Documentation
    Base: http://localhost:5000

1. Add new book
    - Method : POST
    - URL : ```/books```
    - Body Request:
        ```
        {
            "name": string,
            "year": number,
            "author": string,
            "summary": string,
            "publisher": string,
            "pageCount": number,
            "readPage": number,
            "reading": boolean
        }
        ```
    - No name response:
        * Status Code : 400
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Gagal menambahkan buku. Mohon isi nama buku"
            }
            ```
    - readPage > pageCount response:
        * Status Code : 400
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount"
            }
            ```
    - Generic error response:
        * Status Code : 500
        * Response Body:
            ```
            {
                "status": "error",
                "message": "Buku gagal ditambahkan"
            }
            ```
    - Success response:
        * Status Code : 201
        * Response Body:
            ```
            {
                "status": "success",
                "message": "Buku berhasil ditambahkan",
                "data": {
                    "bookId": "1L7ZtDUFeGs7VlEt"
                }
            }
            ```

2. Get all books
    - Method : GET
    - URL: ```/books```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "books": [
                        {
                            "id": "Qbax5Oy7L8WKf74l",
                            "name": "Buku A",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "1L7ZtDUFeGs7VlEt",
                            "name": "Buku B",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "K8DZbfI-t3LrY7lD",
                            "name": "Buku C",
                            "publisher": "Dicoding Indonesia"
                        }
                    ]
                }
            }
            ```

3. Get list read books
    - Method : GET
    - URL: ```/books?reading=1```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "books": [
                        {
                            "id": "Qbax5Oy7L8WKf74l",
                            "name": "Buku A",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "1L7ZtDUFeGs7VlEt",
                            "name": "Buku B",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "K8DZbfI-t3LrY7lD",
                            "name": "Buku C",
                            "publisher": "Dicoding Indonesia"
                        }
                    ]
                }
            }
            ```

4. Get list unread books
    - Method : GET
    - URL: ```/books?reading=0```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "books": [
                        {
                            "id": "Qbax5Oy7L8WKf74l",
                            "name": "Buku A",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "1L7ZtDUFeGs7VlEt",
                            "name": "Buku B",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "K8DZbfI-t3LrY7lD",
                            "name": "Buku C",
                            "publisher": "Dicoding Indonesia"
                        }
                    ]
                }
            }
            ```

5. Get list books with contain name
    - Method : GET
    - URL: ```/books?name=xxx```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "books": [
                        {
                            "id": "Qbax5Oy7L8WKf74l",
                            "name": "xxx",
                            "publisher": "Dicoding Indonesia"
                        }
                    ]
                }
            }
            ```

6. Get list finished books
    - Method : GET
    - URL: ```/books?finished=1```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "books": [
                        {
                            "id": "Qbax5Oy7L8WKf74l",
                            "name": "Buku A",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "1L7ZtDUFeGs7VlEt",
                            "name": "Buku B",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "K8DZbfI-t3LrY7lD",
                            "name": "Buku C",
                            "publisher": "Dicoding Indonesia"
                        }
                    ]
                }
            }
            ```

7. Get list unfinished books
    - Method : GET
    - URL: ```/books?finished=0```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "books": [
                        {
                            "id": "Qbax5Oy7L8WKf74l",
                            "name": "Buku A",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "1L7ZtDUFeGs7VlEt",
                            "name": "Buku B",
                            "publisher": "Dicoding Indonesia"
                        },
                        {
                            "id": "K8DZbfI-t3LrY7lD",
                            "name": "Buku C",
                            "publisher": "Dicoding Indonesia"
                        }
                    ]
                }
            }
            ```

8. Get a book by id
    - Method : GET
    - URL: ```/books/{bookId}```
    - id not found response:
        * Status Code : 404
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Buku tidak ditemukan"
            }
            ```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "data": {
                    "book": {
                        "id": "aWZBUW3JN_VBE-9I",
                        "name": "Buku A Revisi",
                        "year": 2011,
                        "author": "Jane Doe",
                        "summary": "Lorem Dolor sit Amet",
                        "publisher": "Dicoding",
                        "pageCount": 200,
                        "readPage": 26,
                        "finished": false,
                        "reading": false,
                        "insertedAt": "2021-03-05T06:14:28.930Z",
                        "updatedAt": "2021-03-05T06:14:30.718Z"
                    }
                }
            }
            ```

9. Update book data
    - Method : PUT
    - URL : ```/books/{bookId}```
    - Body Request:
        ```
        {
            "name": string,
            "year": number,
            "author": string,
            "summary": string,
            "publisher": string,
            "pageCount": number,
            "readPage": number,
            "reading": boolean
        }
        ```
    - No name response:
        * Status Code : 400
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Gagal memperbarui buku. Mohon isi nama buku"
            }
            ```
    - readPage > pageCount response:
        * Status Code : 400
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount"
            }
            ```
    - id not found response:
        * Status Code : 404
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Gagal memperbarui catatan. Id tidak ditemukan"
            }
            ```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "message": "Buku berhasil diperbarui"
            }
            ```

10. Delete book
    - Method : DELETE
    - URL: ```/books/{bookId}```
    - id not found response:
        * Status Code : 404
        * Response Body:
            ```
            {
                "status": "fail",
                "message": "Buku gagal dihapus. Id tidak ditemukan"
            }
            ```
    - Success response:
        * Status Code : 200
        * Response Body:
            ```
            {
                "status": "success",
                "message": "Buku berhasil dihapus"
            }
            ```
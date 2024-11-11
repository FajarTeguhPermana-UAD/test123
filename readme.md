Berikut adalah tabel yang telah ditambahkan kolom "Actual Result" dan "Status" dengan isi "Berhasil" untuk setiap test case. Tabel ini juga sudah diformat agar mudah disalin.

---

### `ArticleService` Test Suite

| **Test Suite**   | **Test Case**                 | **Description**                                             | **Expected Output**                                           | **Actual Result**                                           | **Status**  |
|------------------|-------------------------------|-------------------------------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------|-------------|
| `ArticleService` | `getAllArticles`              | Returns all articles                                        | Array of articles: `[{ id: '1', title: 'Article 1' }]`       | Array of articles: `[{ id: '1', title: 'Article 1' }]`     | Berhasil    |
|                  | `getArticleById` (existing)   | Returns article with a given ID                             | Article object: `{ id: '1', title: 'Article 1' }`            | Article object: `{ id: '1', title: 'Article 1' }`          | Berhasil    |
|                  | `getArticleById` (non-exist)  | Returns null if no article is found                         | `null`                                                        | `null`                                                      | Berhasil    |
|                  | `createArticle`               | Creates and returns a new article                           | Created article object: `{ id: '123', title: 'New Article' }`| Created article object: `{ id: '123', title: 'New Article' }`| Berhasil |
|                  | `updateArticle` (existing)    | Updates and returns an existing article                     | Updated article object: `{ id: '1', title: 'Updated Article' }`| Updated article object: `{ id: '1', title: 'Updated Article' }` | Berhasil |
|                  | `updateArticle` (non-exist)   | Returns null if the article is not found                    | `null`                                                        | `null`                                                      | Berhasil    |
|                  | `deleteArticle` (existing)    | Deletes and returns an article                              | Deleted article object: `{ id: '1', title: 'Article 1' }`    | Deleted article object: `{ id: '1', title: 'Article 1' }`   | Berhasil    |
|                  | `deleteArticle` (non-exist)   | Returns null if the article is not found                    | `null`                                                        | `null`                                                      | Berhasil    |

---

### `ArticleRepository` Test Suite

| **Test Suite**        | **Test Case**                       | **Description**                                               | **Expected Output**                                               | **Actual Result**                                                 | **Status**  |
|-----------------------|-------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------------|-------------------------------------------------------------------|-------------|
| `ArticleRepository`   | `getAllArticles`                   | Returns all articles                                          | Array of articles: `[{ id: '1', title: 'Article 1' }, { id: '2', title: 'Article 2' }]` | Array of articles: `[{ id: '1', title: 'Article 1' }, { id: '2', title: 'Article 2' }]` | Berhasil |
|                       | `getArticleById` (existing)        | Returns article with a given ID                               | Article object: `{ id: '1', title: 'Article 1' }`                | Article object: `{ id: '1', title: 'Article 1' }`                | Berhasil    |
|                       | `getArticleById` (non-exist)       | Returns null if no article is found                           | `null`                                                            | `null`                                                            | Berhasil    |
|                       | `createArticle`                    | Adds and saves a new article                                  | Created article with new `id`, title: `New Article`, write called | Created article with new `id`, title: `New Article`, write called | Berhasil    |
|                       | `updateArticle` (existing)         | Updates and saves an existing article                         | Updated article object with title: `Updated Article`, write called | Updated article object with title: `Updated Article`, write called | Berhasil |
|                       | `updateArticle` (non-exist)        | Returns null if article to update is not found                | `null`                                                            | `null`                                                            | Berhasil    |
|                       | `deleteArticle` (existing)         | Deletes and returns an article                                | Deleted article object with title: `Article 1`, write called     | Deleted article object with title: `Article 1`, write called     | Berhasil    |
|                       | `deleteArticle` (non-exist)        | Returns null if article to delete is not found                | `null`                                                            | `null`                                                            | Berhasil    |

---

### `Article API Integration Tests`

#### `GET /api/articles`

| **Test Suite**                | **Test Case**                          | **Description**                                    | **Expected Output**                                       | **Actual Result**                                        | **Status**  |
|-------------------------------|----------------------------------------|----------------------------------------------------|-----------------------------------------------------------|----------------------------------------------------------|-------------|
| `GET /api/articles`           | Returns all articles                  | Retrieves all articles from the API                | Status: `200`, Body: `[{ id: '1', title: 'Test Article 1' }]` | Status: `200`, Body: `[{ id: '1', title: 'Test Article 1' }]` | Berhasil |

#### `GET /api/articles/:id`

| **Test Suite**                | **Test Case**                                  | **Description**                                    | **Expected Output**                                               | **Actual Result**                                                | **Status**  |
|-------------------------------|------------------------------------------------|----------------------------------------------------|-------------------------------------------------------------------|------------------------------------------------------------------|-------------|
| `GET /api/articles/:id`       | Retrieves an article by ID (existing)          | Returns a single article by specified ID           | Status: `200`, Body: `{ id: '1', title: 'Test Article 1' }`      | Status: `200`, Body: `{ id: '1', title: 'Test Article 1' }`     | Berhasil    |
|                               | Retrieves an article by ID (non-existent)      | Returns 404 if article ID not found                | Status: `404`, Body: `{ message: 'Article not found' }`          | Status: `404`, Body: `{ message: 'Article not found' }`         | Berhasil    |

#### `POST /api/articles`

| **Test Suite**                | **Test Case**                                  | **Description**                                    | **Expected Output**                                                                                      | **Actual Result**                                               | **Status**  |
|-------------------------------|------------------------------------------------|----------------------------------------------------|----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|-------------|
| `POST /api/articles`          | Creates a new article                          | Adds and returns a new article                     | Status: `201`, Body: `{ id: <new id>, title: 'New Article' }`, file has 2 articles | Status: `201`, Body: `{ id: <new id>, title: 'New Article' }`, file has 2 articles | Berhasil |

#### `PUT /api/articles/:id`

| **Test Suite**                | **Test Case**                                     | **Description**                                    | **Expected Output**                                                       | **Actual Result**                                                   | **Status**  |
|-------------------------------|---------------------------------------------------|----------------------------------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------------|-------------|
| `PUT /api/articles/:id`       | Updates an article by ID (existing)               | Updates and returns an article with specified ID   | Status: `200`, Body: `{ title: 'Updated Article 1' }`, file updated for ID `1` | Status: `200`, Body: `{ title: 'Updated Article 1' }`, file updated for ID `1` | Berhasil |
|                               | Updates an article by ID (non-existent)           | Returns 404 if article to update is not found      | Status: `404`, Body: `{ message: 'Article not found' }`                       | Status: `404`, Body: `{ message: 'Article not found' }`                    | Berhasil |

#### `DELETE /api/articles/:id`

| **Test Suite**                | **Test Case**                                     | **Description**                                    | **Expected Output**                                                          | **Actual Result**                                                 | **Status**  |
|-------------------------------|---------------------------------------------------|----------------------------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------|-------------|
| `DELETE /api/articles/:id`    | Deletes an article by ID (existing)               | Deletes and returns an article with specified ID   | Status: `200`, Body: `{ title: 'Test Article 1' }`, file has no articles     | Status: `200`, Body: `{ title: 'Test Article 1' }`, file has no articles | Berhasil |
|                               | Deletes an article by ID (non-existent)           | Returns 404 if article to delete is not found      | Status: `404`, Body: `{ message: 'Article not found' }`                      | Status: `404`, Body: `{ message: 'Article not found' }`                    | Berhasil |
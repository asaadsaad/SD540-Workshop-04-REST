### SD540-Workshop-04-REST
Add another Schema to the previous homework and upload the student files as follows:
```typescript
// File schema:
const FileSchema = new Schema({
    originalname: { type: String, required: true },
    mimetype: { type: String, required: true },
    path: { type: String, required: true },
    size: { type: Number, required: true }
}, { timestamps: true });

const CourseSchema = new Schema({
    code: { type: String, required: true },
    name: { type: String, required: true },
    description: String,
    deleted: { type: Boolean, default: false }
}, { timestamps: true });

const StudentSchema = new Schema({
    email: { type: String, required: true },
    name: { type: String, required: true },
    courses: [CourseSchema],
    files: [FileSchema],   // <=== Using files schema
    deleted: { type: Boolean, default: false }
}, { timestamps: true });
```

**Install and use the following middlewares to your application:**
* Use [Multer](https://www.npmjs.com/package/multer) middleware, to upload files.
* Use [CORS](https://www.npmjs.com/package/cors) middleware, to allow CORS requests.
* Use [Helmet](https://www.npmjs.com/package/helmet) middleware, to add security headers to your response.
  
To send a file over HTTP, you will need to send a `multipart/form-data` request. You may either use [Postman](https://www.postman.com/) or use the provided [REST Client test file](./test.http).
  
Create a Rest API to perform the following operations on files:
* Upload a new file and save the file details in DB. (use multer `.single(FILE_FORM_NAME)`)
* Get the document details by `_id`.
* Download a file by `_id`, when a query parameter `?download=true` is passed. (use `response.download()`)
* Delete the file by `_id` from DB and file system. (use `fs.unlink()`)

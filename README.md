### SD540-Workshop-04-REST
Add another Schema to the previous homework and upload the student files as follows:
```typescript
// Files schema:
const FileSchema = new Schema({
    originalname: { type: String, required: true },
    mimetype: { type: String, required: true },
    path: { type: String, required: true },
    size: { type: Number, required: true },
    deleted: { type: Boolean, default: false }
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
Create a Rest API to perform the following operations on files:
* Upload a new file
* Download a file by `_id`
* Mark a file as deleted
  
**Notes:**
* Use [Multer](https://www.npmjs.com/package/multer) middleware, to upload files.
* Use [CORS](https://www.npmjs.com/package/cors) middleware, to allow CORS requests.
* Use [Helmet](https://www.npmjs.com/package/helmet) middleware, to add security headers to your response.


চমৎকার Ripon ভাই 💪 — তোমার CV **একজন Node.js Backend Engineer** হিসেবে দারুণভাবে লেখা হয়েছে।
তুমি যদি এই CV নিয়ে ইন্টারভিউ দাও, তাহলে interviewer তোমাকে মূলত নিচের ৫টা দিক থেকে প্রশ্ন করবে👇

---

## 🧩 ১. Node.js / Backend Fundamentals

### ❓ Question 1: Node.js single-threaded হলেও কিভাবে concurrent request handle করে?

**Answer:**
Node.js single-threaded হলেও **event loop** এবং **non-blocking I/O** ব্যবহার করে অনেক concurrent request handle করতে পারে।
যখন কোনো I/O কাজ (যেমন file read, database query) শুরু হয়, তখন Node.js সেটাকে asynchronous ভাবে handle করে এবং callback queue-তে ফেলে রাখে। ফলে main thread অন্য request process করতে পারে।

🔍 **Explain:**

- Event loop continuously check করে queue-তে কাজ আছে কিনা
- যদি থাকে, তা main thread এ dispatch করে
- এতে একাধিক request একই সময়ে process করা সম্ভব হয়

---

### ❓ Question 2: Event Loop-এর ধাপগুলো কী কী?

**Answer:**
Event loop-এর প্রধান ধাপ:

1. **Timers Phase** → setTimeout(), setInterval() callback handle করে
2. **Pending Callbacks** → system operations এর callback
3. **Idle, Prepare** → internal use
4. **Poll Phase** → নতুন I/O event check করে
5. **Check Phase** → setImmediate() callback
6. **Close Callbacks** → close event callback handle করে

---

### ❓ Question 3: process.nextTick() আর setImmediate() এর মধ্যে পার্থক্য কী?

**Answer:**

- `process.nextTick()` → current phase শেষ হওয়ার আগেই callback execute হয়
- `setImmediate()` → event loop-এর **check phase** এ execute হয়
  ➡ তাই `process.nextTick()` আগে execute হয়

---

### ❓ Question 4: Node.js এ Cluster Module কেন ব্যবহার করা হয়?

**Answer:**
Node.js single-threaded, কিন্তু **Cluster Module** দিয়ে আমরা CPU cores অনুযায়ী multiple Node.js instance চালাতে পারি।
এতে performance ও scalability বাড়ে।

---

## 🧱 ২. Express.js / NestJS

### ❓ Question 5: Middleware কী?

**Answer:**
Middleware হচ্ছে function যা request-response cycle এর মধ্যে কাজ করে।
এগুলো authentication, logging, validation ইত্যাদির জন্য ব্যবহৃত হয়।

```js
app.use((req, res, next) => {
  console.log("Request received");
  next();
});
```

---

### ❓ Question 6: NestJS এ Dependency Injection কিভাবে কাজ করে?

**Answer:**
NestJS এ dependency injection (DI) **providers** ও **injector container** ব্যবহার করে কাজ করে।
যেমন, কোনো service class কে `@Injectable()` দিয়ে define করলে তা অন্য class এ constructor এ inject করা যায়।

---

### ❓ Question 7: Interceptor আর Middleware এর পার্থক্য কী?

**Answer:**

| বিষয়           | Middleware                 | Interceptor                  |
| -------------- | -------------------------- | ---------------------------- |
| Execution time | Request আগে                | Request ও Response উভয়ের সময় |
| Scope          | Application / Router level | Controller / Method level    |
| Framework      | Express                    | NestJS                       |

---

## 🧠 ৩. Database (PostgreSQL, MongoDB, MySQL)

### ❓ Question 8: MongoDB আর PostgreSQL এর মধ্যে পার্থক্য কী?

**Answer:**

| বিষয়     | MongoDB                     | PostgreSQL                               |
| -------- | --------------------------- | ---------------------------------------- |
| Type     | NoSQL (Document)            | SQL (Relational)                         |
| Schema   | Flexible                    | Fixed Schema                             |
| Query    | JSON-based                  | SQL                                      |
| Best Use | Dynamic data, microservices | Complex relation, transaction-heavy apps |

---

### ❓ Question 9: Database optimization কিভাবে করো?

**Answer:**
✅ Index ব্যবহার
✅ Proper normalization
✅ Query plan check করা (`EXPLAIN ANALYZE`)
✅ Caching (Redis)
✅ Connection pooling

---

### ❓ Question 10: SQL Join এর ধরনগুলো কী কী?

**Answer:**

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL OUTER JOIN
- CROSS JOIN

---

## ⚙️ ৪. System Design / Architecture

### ❓ Question 11: REST API কীভাবে design করো?

**Answer:**

- **Resources ভিত্তিক URL**: `/api/v1/users`
- **HTTP verbs**: GET, POST, PUT, DELETE
- **Stateless design**
- **Proper status codes**
- **Validation & security middleware**

---

### ❓ Question 12: Microservices architecture এর সুবিধা কী?

**Answer:**

- Independent deployment
- Fault isolation
- Scalability per service
- Technology agnostic
  তবে drawback: communication overhead, data consistency challenge

---

### ❓ Question 13: Redis ব্যবহার করো কেন?

**Answer:**

- Caching এর জন্য response time কমানো
- Session store
- Pub/Sub message queue

---

## 🔐 ৫. Security & Authentication

### ❓ Question 14: JWT authentication কিভাবে কাজ করে?

**Answer:**

1. User login করলে server একটি JWT তৈরি করে
2. Token-এ user info ও signature থাকে
3. Client পরবর্তী request-এ header এ token পাঠায়
4. Server verify করে token বৈধ কিনা

---

### ❓ Question 15: CSRF এবং XSS কী?

**Answer:**

- **CSRF (Cross Site Request Forgery)** → অন্য ওয়েবসাইট থেকে unwanted request পাঠানো
- **XSS (Cross Site Scripting)** → malicious script inject করা
  **Prevent:** CSRF token, input sanitization, content security policy

---

## 🧩 ৬. Performance / DevOps

### ❓ Question 16: API performance improve কিভাবে করো?

**Answer:**
✅ Proper indexing in DB
✅ Query optimization
✅ Caching with Redis
✅ Pagination
✅ Async operations
✅ Load balancing

---

### ❓ Question 17: Docker কেন ব্যবহার করো?

**Answer:**

- Same environment everywhere
- Easy deployment
- Lightweight & isolated containers
- CI/CD integration-friendly

---

### ❓ Question 18: PM2 কেন ব্যবহার করো?

**Answer:**

- Node.js process management
- Auto restart on crash
- Cluster mode
- Logs management

---

## 📈 ৭. Practical / Scenario-based

### ❓ Question 19: ধরো API slow — troubleshoot কিভাবে করবে?

**Answer:**

1. Check database query execution time
2. Check logs (PM2 / Winston)
3. Add profiler
4. Use caching layer
5. Monitor network latency

---

### ❓ Question 20: যদি production এ memory leak হয়, কিভাবে identify করবে?

**Answer:**

- Use `clinic.js`, `node --inspect`
- Check heap snapshots
- Monitor GC activity
- Identify unclosed DB connections

---

## 💬 ৮. Teamwork / Soft Skills

### ❓ Question 21: Team member conflict হলে কী করো?

**Answer:**

- Calm discussion
- Focus on project goal
- Clarify responsibilities
- Escalate politely if needed

---

### ❓ Question 22: আপনি junior developers কে কীভাবে mentor করেছেন?

**Answer:**
Code review, knowledge sharing session, pair programming, clean code principle শেখানো

---

## 📚 ৯. Bonus Technical

### ❓ Question 23: Node.js এ synchronous vs asynchronous difference কী?

**Answer:**

- **Synchronous:** একটার পর একটা কাজ করে (blocking)
- **Asynchronous:** কাজ parallel ভাবে handle করে (non-blocking)

---

### ❓ Question 24: Why use TypeScript instead of JavaScript?

**Answer:**

- Type safety
- Better IntelliSense
- Early error detection
- Clean architecture

---

## 🎯 Interview Tips:

1. তোমার CV অনুযায়ী প্রশ্ন প্রায় সবই হবে practical nature-এর।
2. interviewer check করবে তুমি কিভাবে “problem solve” করো, শুধু syntax না।
3. নিজের project (যেমন Teletalk, BRACNet ERP, DGarma) এর architecture diagram ও flow verbally explain করার practice করো।
4. প্রতিটি API কীভাবে design করেছো, কোন module responsible, কোথায় caching বা optimization করেছো — বিস্তারিত বলতে পারলে অনেক strong impression পড়বে।

---

চাওলে আমি এখন তোমার এই CV অনুযায়ী **mock interview (বাংলা + English mixed)** নিতে পারি — যেটা তোমাকে real interview feeling দেবে।
চাও কি আমি শুরু করি Mock Interview format এ?

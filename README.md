# Nexa Contact Email API

Start the API from this folder:

```bash
npm start
```

The server listens on port `3000` by default. Configure Hostinger SMTP credentials in your local `.env` file (see `.env.example`). Contact submissions are delivered to `CONTACT_TO` (or `SMTP_USER` if `CONTACT_TO` is omitted).

## Send a contact email

**Endpoint:** `POST http://localhost:3000/api/contact`

**Headers:** `Content-Type: application/json`

**JSON body:**

```json
{
  "name": "Sridhar Bathula",
  "company": "test",
  "email": "sridharbathula2002@gmail.com",
  "phone": "9876543210",
  "interest": "dfd",
  "message": "sdfgd"
}
```

Example browser call:

```js
const response = await fetch("http://localhost:3000/api/contact", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    name: "Sridhar Bathula",
    company: "test",
    email: "sridharbathula2002@gmail.com",
    phone: "9876543210",
    interest: "dfd",
    message: "sdfgd"
  })
});

const result = await response.json();
console.log(result);
```

On success the API returns `200` with `{ "message": "Contact email sent successfully" }`. Missing or invalid fields return `400`; SMTP configuration or delivery failures return `503` or `502`.

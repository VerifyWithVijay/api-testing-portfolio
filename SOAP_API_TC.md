# 📘 ISBN SOAP API – Test Cases

## 🧩 API Details
**Endpoint:** `https://webservices.daehosting.com/services/isbnservice.wso`  
**Operation:** `IsValidISBN10`  
**Protocol:** SOAP / JSON  
**Purpose:** Validates whether an ISBN-10 number is valid or not.

---

## ✅ Positive Test Cases

| Test Case ID | Test Case Description | Pre-Condition | Test Steps | Expected Result | Actual Result | Status |
|---------------|----------------------|----------------|-------------|----------------|----------------|---------|
| TC_API_001 | Validate a correct ISBN number | API endpoint is reachable | Send request with `sISBN=935333845X` | Response code: 200 OK<br>Response body: `true` |  |  |
| TC_API_002 | Validate ISBN with numeric value only | API endpoint is reachable | Send request with `sISBN=1234567890` | Response code: 200 OK<br>Response body: `false` |  |  |
| TC_API_003 | Validate ISBN ending with X (valid case) | API endpoint is reachable | Send request with `sISBN=047195869X` | Response code: 200 OK<br>Response body: `true` |  |  |
| TC_API_004 | Validate ISBN ending with lowercase x (valid case) | API endpoint is reachable | Send request with `sISBN=047195869x` | Response code: 200 OK<br>Response body: `true` |  |  |
| TC_API_005 | Validate ISBN using JSON request format | API endpoint is reachable | Send JSON body `{"sISBN": "935333845X"}` | Response code: 200 OK<br>Response body: `true` |  |  |

---

## ❌ Negative Test Cases

| Test Case ID | Test Case Description | Pre-Condition | Test Steps | Expected Result | Actual Result | Status |
|---------------|----------------------|----------------|-------------|----------------|----------------|---------|
| TC_API_006 | Validate ISBN with less than 10 digits | API endpoint is reachable | Send request with `sISBN=12345` | Response code: 200 OK<br>Response body: `false` or validation error |  |  |
| TC_API_007 | Validate ISBN with more than 10 digits | API endpoint is reachable | Send request with `sISBN=1234567890123` | Response code: 200 OK<br>Response body: `false` |  |  |
| TC_API_008 | Validate ISBN with special characters | API endpoint is reachable | Send request with `sISBN=1234@#$567` | Response code: 400 Bad Request<br>Error message in response |  |  |
| TC_API_009 | Validate ISBN with blank input | API endpoint is reachable | Send request with `sISBN=` (empty) | Response code: 400 Bad Request<br>Error message displayed |  |  |
| TC_API_010 | Validate ISBN with null input | API endpoint is reachable | Send request without ISBN tag/value | Response code: 400 Bad Request<br>Error message displayed |  |  |
| TC_API_011 | Validate ISBN with invalid Content-Type | API endpoint is reachable | Send request with `Content-Type: text/plain` | Response code: 415 Unsupported Media Type |  |  |
| TC_API_012 | Validate request with empty SOAP body | API endpoint is reachable | Send request with empty `<soap:Body>` | Response code: 400 Bad Request |  |  |
| TC_API_013 | Validate request with invalid XML structure | API endpoint is reachable | Send malformed XML request | Response code: 400 Bad Request |  |  |
| TC_API_014 | Validate request with wrong method (GET) | API endpoint is reachable | Send GET request instead of POST | Response code: 405 Method Not Allowed |  |  |
| TC_API_015 | Validate response for invalid host | API endpoint is not reachable | Send request to wrong domain | Response code: Connection Error or 404 Not Found |  |  |

---

## 🧾 Notes
- Test using **SOAP UI** or **Postman (SOAP body or raw XML)**  
- Verify both **SOAP 1.1** and **SOAP 1.2** versions  
- Optional JSON-based validation for same operation  
- Check response headers: `Content-Type`, `Content-Length`, `Status`  

---

## 🧠 Example SOAP Request (for reference)
```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <IsValidISBN10 xmlns="http://webservices.daehosting.com/ISBN">
      <sISBN>935333845X</sISBN>
    </IsValidISBN10>
  </soap:Body>
</soap:Envelope>


---

## 🚀 How to Run Automation Tests

### **For Java (Rest Assured)**
```bash
# Clone the repository
git clone https://github.com/<your-username>/api-testing-portfolio.git
cd api-testing-portfolio/automation/rest-assured

# Run tests using Maven
mvn clean test


---

Author: **Vijay Kamisetty**
💼 18+ Years QA Experience | Building API Testing Portfolio
📧 ravindra.kamisetty@gmail.com
🔗 https://www.linkedin.com/in/vijay-kamisetty 


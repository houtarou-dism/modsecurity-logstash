# modsecurity-logstash

Logstash grok filters for parsing modsecurity audit logs.

## Fields

Fields that can be parsed by grok filter

### Section A

audit log header

<details>
    <summary>An example log</summary>
    
    [05/Jan/2021:18:48:51 +0000] 1609840131 192.168.30.10 31943 192.168.10.10 80
</details>

* log_date
* unique_transaction_id
* source
  * ip
  * port
* destination
  * ip
  * port

### Section B

request headers

* request
  * header
    * http_method
    * http_version
    * accept
    * cache_control
    * user_agent
    * content_type
    * referer
    * origin
    * upgrade_insecure_requests
    * content_length
    * connection
    * host
    * accept_encoding
    * cookie
    * accept_language
  * url

### Section E

intended response body

* intended_response
  * body

### Section F

response headers

* response
  * headers
    * http_version
    * http_status
    * server
    * date
    * content_length
    * content_type
    * connection

### Section H

audit log trailer.

Up to 10 can be analyzed.

<details>
    <summary>An example log</summary>
    
    ModSecurity: Warning. Matched "Operator `Rx' with parameter `^[\d.:]+$' against variable `REQUEST_HEADERS:Host' (Value: `54.183.57.254' ) [file "/usr/local/owasp-modsecurity-crs-3.2.0/rules/REQUEST-920-PROTOCOL-ENFORCEMENT.conf"] [line "678"] [id "920350"] [rev ""] [msg "Host header is a numeric IP address"] [data "54.183.57.254"] [severity "4"] [ver "OWASP_CRS/3.2.0"] [maturity "0"] [accuracy "0"] [tag "application-multi"] [tag "language-multi"] [tag "platform-multi"] [tag "attack-protocol"] [tag "OWASP_CRS"] [tag "OWASP_CRS/PROTOCOL_VIOLATION/IP_HOST"] [tag "WASCTC/WASC-21"] [tag "OWASP_TOP_10/A7"] [tag "PCI/6.5.10"] [hostname "10.0.1.10"] [uri "/input"] [unique_id "1609840121"] [ref "o0,12v27,12"]
</details>

* audit_log
  * 1
    * action
    * message1
    * file
    * id
    * message2
    * data
    * unique_id




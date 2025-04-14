# Approval Center Callback Signature Verification

When an Approval Center user approves or rejects an approval item, SeaTalk Open Platform will send a callback request to the approve\_url or reject\_url of this approval item. To ensure that a callback request is secure, authentic and indeed sent by SeaTalk Open Platform, the "Authorization" header of the request (the remote signature) can be compared with a local signature calculated by you.

The local signature is calculated by incorporating different elements such as the request parameters. Below are 2 code demos written in Python and Go to help you verify the authenticity of a callback request. In the demos, an HTTP request is received and broken down to calculate the local signature. Then, the local signature is compared with the remote signature to verify the request.

# Python Demo

```python
import base64
import hashlib
import hmac
from urllib import parse

from flask import Flask, request

app = Flask(__name__)

sop_app_secret = '__secret_of_your_app__'


@app.route('/<path:path>', methods=('POST',))
def approval_callback(path):
         local_sign = sign(
                  sop_app_secret,
                  request.method,
                  request.path,
                  request.content_type or '',
                  request.data,
                  request.headers.get('Date', default=''),
                  request.headers.get('X-Token', default=''),
                  request.args.items())
         remote_sign = request.headers.get('Authorization', default='').split(' ')[-1]
         print(f'local signature: {local_sign}')
         print(f'remote signature: {remote_sign}')
         print('Correct!' if local_sign == remote_sign else 'Not match!')
         return {'code': 0}

def sign(secret, method, path, content_type, body, date, x_token, params):
         content_md5 = hashlib.md5(body).hexdigest() if body else ''
         headers_string = f'x-token:{x_token}' if x_token else ''
         params_string = '&'.join(map(
                  lambda x: f'{parse.quote(x[0])}={parse.quote(x[1])}',
                  sorted(params)))
         signature_string = f'{method}\n' \
                                         f'{path}\n' \
                                         f'{content_type}\n' \
                                         f'{content_md5}\n' \
                                         f'{date}\n' \
                                         f'{headers_string}\n' \
                                         f'{params_string}'
         print('--- base string ---')
         print(signature_string)
         print('--- base string end ---')
         signature_hmac = hmac.new(secret.encode('utf-8'),
                                                             signature_string.encode('utf-8'), 'sha1')
         s = bytes.decode(base64.b64encode(signature_hmac.digest()))
         return s

if __name__ == '__main__':
         app.run(debug=True, host='0.0.0.0', port=8080) Copy
```

# Go Demo

```python
package main


import (
    "bytes"
    "crypto/hmac"
    "crypto/md5"
    "crypto/sha1"
    "encoding/base64"
    "encoding/hex"
    "fmt"
    "io"
    "io/ioutil"
    "net/http"
    "net/url"
    "sort"
    "strings"
)


const sopAppSecret = "__secret_of_your_app__"


func main() {
    http.HandleFunc("/", approvalCallback)
    if err: = http.ListenAndServe(":8080", nil);
    err != http.ErrServerClosed {
        panic(err)
    }
}


func approvalCallback(w http.ResponseWriter, req * http.Request) {
    localSign, err: = sign(req, sopAppSecret)
    if err != nil {
        panic(err)
    }
    remoteSign: = strings.TrimPrefix(req.Header.Get("Authorization"), "Signature ")
    fmt.Println("local signature: ", localSign)
    fmt.Println("remote signature: ", remoteSign)
    if localSign == remoteSign {
        fmt.Println("Correct!")
    } else {
        fmt.Println("Not match!")
    }
    _, _ = io.WriteString(w, "{\"code\": 0}")
}


func sign(req * http.Request, secret string)(string, error) {
    buf: = bytes.NewBuffer(nil)
        // VERB
    _,
    _ = fmt.Fprintf(buf, "%s\n", req.Method)
    // Path
    _,
    _ = fmt.Fprintf(buf, "%s\n", req.URL.EscapedPath())
    // Content-Type
    _,
    _ = fmt.Fprintf(buf, "%s\n", req.Header.Get("Content-Type"))
    // Content-Md5
    var contentMD5 string
    b,
    err: = ioutil.ReadAll(req.Body)
    if err != nil {
        return "", err
    }
    req.Body = ioutil.NopCloser(bytes.NewBuffer(b)) // put body back
    if len(b) > 0 {
        h: = md5.New()
        _,
        err = h.Write(b)
        if err != nil {
            return "", err
        }
        contentMD5 = hex.EncodeToString(h.Sum(nil))
    }
    _,
    _ = fmt.Fprintf(buf, "%s\n", contentMD5)
    // Date
    date: = req.Header.Get("Date")
    _,
    _ = fmt.Fprintf(buf, "%s\n", date)
    // X-Token header
    var headersStr string
    if xToken: = req.Header.Get("X-Token");xToken != "" {
        headersStr = fmt.Sprintf("x-token:%s", xToken)
    }
    _,
    _ = fmt.Fprintf(buf, "%s\n", headersStr)
    // Query params
    q: = req.URL.Query()
    keys: = make([] string, 0, len(q))
    for k: = range q {
        keys = append(keys, k)
    }
    sort.Strings(keys)
    var a bool
    for _,
    k: = range keys {
        keyEscaped: = url.QueryEscape(k)
        values: = q[k]
        sort.Strings(values)
        for _,
        v: = range values {
            if v != "" {
                if a {
                    _ = buf.WriteByte('&')
                }
                _, _ = buf.WriteString(keyEscaped)
                _ = buf.WriteByte('=')
                _, _ = buf.WriteString(url.QueryEscape(v))
                a = true
            }
        }
    }
    if len(q) > 0 {
        _, _ = fmt.Fprintf(buf, "%s", q.Encode())
    }
    fmt.Println("--- base string ---")
    fmt.Println(buf.String())
    fmt.Println("--- base string end ---")
    mac: = hmac.New(sha1.New, [] byte(secret))
    mac.Write(buf.Bytes())
    signature: = base64.StdEncoding.EncodeToString(mac.Sum(nil))


    return signature,
    nil
} Copy
```

Was this document helpful?

No

Yes
# Example with a single file

```
POST .../upload
Content-Type: multipart/mixed; charset=utf-8; boundary="---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91"
 
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
Content-Type: application/pdf; charset=utf-8
Content-Disposition: form-data; name="companyReport"; filename="companyReport-2016-03-10.pdf"
 
<file data>
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
```

# Example with multiple files
```
POST .../upload
Content-Type: multipart/mixed; charset=utf-8; boundary="---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91"
 
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
Content-Type: application/pdf; charset=utf-8
Content-Disposition: form-data; name="companyReportPDF"; filename="companyReport-2016-03-10.pdf"
 
<file data>
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet; charset=utf-8
Content-Disposition: form-data; name="companyReportXLSX"; filename="companyReport-2016-03-10.xlsx"
 
<file data>
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
```

# Example with a specific encoding: compressed file
```
POST .../upload
Content-Type: multipart/mixed; charset=utf-8; boundary="---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91"
 
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
Content-Type: application/pdf; charset=utf-8
Content-Disposition: form-data; name="companyReport"; filename="companyReport-2016-03-10.pdf"
Content-Encoding: gzip
 
<gzipped file data>
---------------------------d0b473e2-0abf-433e-8c74-faee35ab6e91
```
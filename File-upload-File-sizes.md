When adding file upload support to your API, one thing that you MUST consider is the size of the files. You must be aware that file size will have an impact on the performance of your application and also that there are specific limitations to consider.

If the Web Application Firewall (WAF) in front of the API should inspect the files (e.g., antivirus/antimalware check), then the files SHOULD NOT be larger than 20MB.

If no antivirus/antimalware checks have to be performed on the uploaded files then you MAY accept larger files, but you MUST pay careful attention to how those files are handled so as to avoid putting too much (memory/CPU) pressure on the WAF and/or on your API.

For large files (>100MB), it MAY be more adequate to consider using SFTP.
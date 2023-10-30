# Steps

### How does it work

- A Key Encrypting Key (KEK) is created and stored in Azure KeyVault
- When creating a new **encrypted file**, a random Data Encryption Key (DEK) is created, encrypted with the KEK
- The Encrypted DEK is then stored as metadata in the **encrypted file**

### Setup SOPS config

Review `.sops.yaml`


### Create new file to be encrypted

Create file
```
touch mycredentials.dev.json
```

Populate ...

### Encrypt file

Output to console
```
sops -e mycredentials.dev.json
```

Output to same file
```
sops -e -i mycredentials.dev.json
```

### Decrypt file

Output to console
```
sops -d mycredentials.dev.json
```

Output to same file
```
sops -d -i mycredentials.dev.json
```


### Key Rotation

Specify a CSV of KMS URIs in the `.sops.yaml` > `creation_rules`

Run the "Rotate" command
```
sops -r example.json
```


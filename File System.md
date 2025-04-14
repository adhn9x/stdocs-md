# File System

## File System

This package provides native filesystem actions for your app

### Useful Type Declarations

These are some of the defined types that are used in the APIs described below. You will need to use them extensively.

|Type|Description|Value|
|---|---|---|
|FileType|This type is used to describe the nature of the file i.e whether is needs to be permanent ( 'document' type) or stored as a cache file (' cache ' type) which may be occasionally cleaned up by the system.|1. 'cache' 2. 'document'|
|Encoding|This type is used to describe the encoding used when reading/writing the contents of a file.|1. 'utf8' 2. 'ascii' 3. 'base64'|

#### interface FileInfo

```javascript
interface FileInfo {
    type: FileType;
    path: string;
} Copy
```

Description  
An interface that encapsulates related file system information of a file. A type that captures headers that need to be passed for network requests. Name refers to the name of the header, followed by the corresponding value  
Parameters

|Parameter|Type|Description|
|---|---|---|
|type|FileType|Information regarding the file type (refer to above FileType)|
|path|string|Path to the file|

### API

interface FileManager  
The IFileManager interface describes the API provided for you to make use of native filesystem capabilities. The FileSystemClient conforms to this interface. Interface that provides native filesystem capabilities.

methods `readFile`

```javascript
readFile(fileInfo: FileInfo, encoding?: Encoding) => Promise<string> Copy
```

Description  
Reads the contents of the file described by*fileInfo*under*encoding,*and returns the contents as a string.  
Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the file.|
|encoding|Encoding?|The encoding value used to read the file. This value is optional, defaults to 'base64'|

methods `writeFile`

```javascript
writeFile(fileInfo: FileInfo, contents: string, encoding?: Encoding) => Promise<void> Copy
```

Description  
Writes the*contents*of the file described by*fileInfo*under*encoding*Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the file.|
|contents|string|The contents to be written to the file.|
|encoding|Encoding?|The encoding value used to write the file. This value is optional, defaults to 'base64'|

methods `moveFile`

```javascript
moveFile(source: FileInfo, destination: FileInfo) => Promise<void> Copy
```

Description  
Moves the file specified by*source*, to*destination.*Parameters

|Parameter|Type|Description|
|---|---|---|
|source|FileInfo|The fileInfo describing the source file.|
|destination|FileInfo|The fileInfo describing the destination file|

methods `copyFile`

```javascript
copyFile(source: FileInfo, destination: FileInfo) => Promise<void> Copy
```

DescriptionCopies the file specified by*source*, to*destination.*Parameters

|Parameter|Type|Description|
|---|---|---|
|source|FileInfo|The fileInfo describing the source file.|
|destination|FileInfo|The fileInfo describing the destination file|

methods `readDir`

```javascript
readDir(fileInfo: FileInfo) => Promise<string[]> Copy
```

DescriptionReads the contents of directory specified by*fileInfo*, if any. Returns a list of file/directory names contained if successful.  
Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the directory|

methods `mkDir`

```javascript
mkDir(fileInfo: FileInfo) => Promise<void> Copy
```

Description  
Makes a directory at the destination specified by*fileInfo*Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the location of the directory|

methods `removeDir`

```javascript
remove(fileInfo: FileInfo) => Promise<void> Copy
```

DescriptionDeletes the file/directory specified by*fileInfo*Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the file/directory|

methods `exists`

```javascript
exists(fileInfo: FileInfo) => Promise<boolean> Copy
```

Description  
Checks if a file/directory exists at the path specified by*fileInfo.*Returns true if that is the case, false otherwise  
Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the file/directory|

methods `getFullURI`

```javascript
getFullURI(fileInfo: FileInfo) => Promise<string> Copy
```

Description  
Provides the full file URI as a string for the file/directory specified by*fileInfo*, if any.  
Parameters

|Parameter|Type|Description|
|---|---|---|
|fileInfo|FileInfo|The fileInfo describing the file/directory|

methods `downloadFile`

```javascript
downloadFile(fromURL: string, destination: FileInfo, headers: Headers | undefined) => Promise<number> Copy
```

Description  
Downloads the contents of*fromURL*to the file at*destination*, while providing any*headers*needed in the download request. Returns a Promise with the result being the HTTP Status code.  
Parameters

|Parameter|Type|Description|
|---|---|---|
|fromURL|string|The URL containing the data to be downloaded|
|destination|FileInfo|The fileInfo describing the destination file|
|headers|Headers \| undefined|Optional headers that will be passed in when making the download request|

Was this document helpful?

No

Yes
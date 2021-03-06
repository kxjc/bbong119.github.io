
# DBR_OutputSettingsToString
Output runtime settings to a string.

```c
DBR_API int DBR_OutputSettingsToString (void* barcodeReader, char content[], const int contentLen, const char* pSettingsName)
```   

---
   
#### Parameters
`[in] barcodeReader` Handle of the barcode reader instance.  
`[in,out]	content` The output string which stores the contents of current settings.   
`[in]	contentLen` The length of output string.   
`[in]	pSettingsName` A unique name for declaring current runtime settings.  


#### Return value
Returns error code (returns 0 if the function operates successfully).    
*You can call [`DBR_GetErrorString`](DBR_GetErrorString.md) to get detailed error message.*

---

#### Code Snippet
```c
void* barcodeReader = DBR_CreateInstance();
DBR_InitLicense(barcodeReader, "t0260NwAAAHV***************");
char errorMessageInit[256];
char errorMessageAppend[256];
DBR_InitRuntimeSettingsWithFile(barcodeReader, "C:\\Program Files (x86)\\Dynamsoft\\{Version number}\\Templates\\RuntimeSettings.json", CM_OVERWRITE, errorMessageInit, 256);
DBR_AppendTplStringToRuntimeSettings(barcodeReader, "{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}", CM_IGNORE, errorMessageAppend, 256);
char pContent[256];
DBR_OutputSettingsToString(barcodeReader, pContent, 256, "currentRuntimeSettings");
DBR_DestroyInstance(barcodeReader);
```


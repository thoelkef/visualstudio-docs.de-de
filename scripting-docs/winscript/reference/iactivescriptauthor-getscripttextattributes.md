---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
Gibt die Textattribute für einen Skriptblock zurück.  
  
## Syntax  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### Parameter  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] Der Text des Skriptblocks.  Diese Zeichenfolge muss nicht NULL sein beendet.  
  
 `cch`  
 \[in\] Die verwendete Größe für die `pszCode` und `pattr`\-Parameter.  
  
 `pszDelimiter`  
 \[in\] Die Adresse des Ende\-vonSkript Trennzeichens.  Wenn `pszCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen \(wie zwei einfache Anführungszeichen\), um das Ende des Skriptlets zu erkennen.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn kein Trennzeichen gibt, zum Ende des Skriptblocks zu identifizieren.  
  
 `dwFlags`  
 \[in\] Die Flags, die mit den Textattributen des Skriptblocks zugeordnet werden.  Kann eine Kombination der folgenden Werte:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Identifizieren Sie Bezeichner, die das SOURCETEXT\_ATTR\_IDENTIFIER\-Attribut haben, und identifizieren Sie Punktoperatoren, die das SOURCETEXT\_ATTR\_MEMBERLOOKUP\-Attribut haben.|  
|GETATTRFLAG\_THIS|0x0100|Identifizieren Sie das aktuelle Objekt, das das SOURCETEXT\_ATTR\_THIS\-Attribut verfügt.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Identifizieren Sie Zeichenfolgeninhalt und Kommentartext, der das SOURCETEXT\_ATTR\_HUMANTEXT\-Attribut verfügt.|  
  
 `pattr`  
 \[out in size\_is \(`cch`\)\] Die Farbinformationen für den Skriptblockcode.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE\_TEXT\_ATTR\-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)
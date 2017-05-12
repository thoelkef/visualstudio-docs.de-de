---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
Gibt den Pfad der Hilfedatei und der Kontexts\-ID des Themas zurück, das den Fehler erläutert, wenn möglich.  
  
## Syntax  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### Parameter  
 `pbstrFileName`  
 \[out\] können Sie die mit dem vollqualifizierten Pfad der Hilfedatei auf.  Wenn keine Hilfedatei gibt, oder ein Fehler auftritt, ist der Rückgabewert NULL.  
  
 `pdwContext`  
 \[out\] Die Hilfekontext\-id für den Fehler.  Wenn keine Hilfedatei gibt \(wenn `pbstrFileName` NULL ist\), hat dieser Parameter keine Bedeutung.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Ein anbieterspezifischer Fehler ist aufgetreten.|  
|`E_INVALIDARG`|`pbstrFileName` oder `pdwContext` waren NULL.|  
|`E_OUTOFMEMORY`|Der Anbieter konnte nicht vom, ausreichend Speicher zuzuordnen, in dem den Hilfedateipfad zurückgeben.|  
  
## Hinweise  
 Diese Methode gibt den Pfad der Hilfedatei und der Kontexts\-ID des Themas zurück, das den Fehler erläutert, wenn möglich.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## Siehe auch  
 [IDispError\-Schnittstelle](../../winscript/reference/idisperror-interface.md)
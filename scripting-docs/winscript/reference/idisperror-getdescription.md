---
title: "IDispError::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetDescription
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetDescription"
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetDescription
Gibt eine Textbeschreibung des Fehlers zurück.  
  
## Syntax  
  
```  
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### Parameter  
 `pbstrDescription`  
 \[out\] Zeichenfolge, die eine kurze Beschreibung des Fehlers enthält.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Text wird in der Sprache zurückgegeben, die durch den Gebietsschemabezeichner \(LCID\) angegeben wird, der an die `IDispatchEx::InvokeEx` für die Methode übergeben wurde, für die den Fehler antraf.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## Siehe auch  
 [IDispError\-Schnittstelle](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)
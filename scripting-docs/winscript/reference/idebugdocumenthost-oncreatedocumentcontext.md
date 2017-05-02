---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
Benachrichtigt den Host, dass ein Kontext des neuen Dokuments erstellt und es dem Host, um ein steuerndes unbekannt für den neuen Kontext optional zurückzugeben.  
  
## Syntax  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### Parameter  
 `ppunkOuter`  
 \[out\] Ein Objekt, das den neuen Kontext steuert.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host stellt kein steuerndes Objekt.|  
  
## Hinweise  
 Diese Methode ermöglicht es dem Host, um neue Funktionen hinzuzufügen Hilfe\-zurVerfügung kann Dokumentenkontexte.  Diese Methode gibt möglicherweise **E\_NOTIMPL** NULL oder ein äußeres Objekt zurück, in diesem Fall der Aufrufer zum Erstellen des Kontexts verantwortlich ist.  
  
## Siehe auch  
 [IDebugDocumentHost\-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)
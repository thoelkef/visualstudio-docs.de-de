---
title: "IDebugDocumentHost::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetPathName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetPathName"
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetPathName
Gibt den vollständigen Pfad und Dateinamen der Quelldatei des Dokuments zurück.  
  
## Syntax  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### Parameter  
 `pbstrLongName`  
 \[out\] Eine Zeichenfolge, die den langen Namen enthält.  
  
 `pfIsOriginalFile`  
 \[out\] Ein Flag, das zutrifft, wenn `pbstrLongName` die ursprüngliche Datei für das Dokument bezieht; andernfalls false.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Keine Quelldatei kann erstellt oder bestimmt werden.|  
  
## Hinweise  
 Diese Methode gibt den vollständigen Pfad und Dateinamen der Quelldatei des Dokuments zurück.  
  
## Siehe auch  
 [IDebugDocumentHost\-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)
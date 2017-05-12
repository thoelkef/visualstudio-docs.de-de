---
title: "IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetPathName"
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetPathName
Gibt den vollständigen Pfad und Dateinamen des Dokuments zurück.  
  
## Syntax  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### Parameter  
 `pbstrLongName`  
 \[out\] können Sie die mit dem vollständigen Pfad und den Dateinamen auf.  
  
 `pfIsOriginalFile`  
 \[out\] boolescher Wert, der angibt, ob der Pfad und der Dateiname das Originaldokument verweisen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Quelldatei kann nicht erstellt werden oder bestimmt werden.|  
  
## Hinweise  
 Diese Methode gibt den vollständigen Pfad und Dateinamen des Dokuments zurück.  
  
 Wenn `pfIsOriginalFile` FALSCH ist, können der Pfad und der Dateiname in `pbstrLongName` eine neu erstellte temporäre Datei an.  
  
## Siehe auch  
 [IDebugDocumentTextExternalAuthor\-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)
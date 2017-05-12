---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
Gibt den sprachabhängigen Programmbezeichner für die Klasse oder die Anwendung zurück, die den Fehler ausgelöst hat.  
  
## Syntax  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### Parameter  
 `pbstrSource`  
 \[out\] verbinden Sie, der einen Programmbezeichner enthält, in der Form `progname.objectname` auf.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird verwendet, um die Klasse oder die Anwendung bestimmen, in der die Ausnahme aufgetreten ist.  Der programmgesteuerte Bezeichner wird in der Sprache zurückgegeben werden, die durch den Gebietsschemabezeichner \(LCID\) angegeben wurde angegeben zum Zeitpunkt des Aufrufs.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## Siehe auch  
 [IDispError\-Schnittstelle](../../winscript/reference/idisperror-interface.md)
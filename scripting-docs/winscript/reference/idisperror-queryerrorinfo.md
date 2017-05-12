---
title: "IDispError::QueryErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::QueryErrorInfo"
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::QueryErrorInfo
Ruft Fehlertypinformationen bestimmten ab.  
  
## Syntax  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### Parameter  
 `guidErrorType`  
 \[in\] GUIDs, die Fehlertyp angibt.  
  
 `ppde`  
 \[out\] Gibt das IDispError\-Objekt an.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die `QueryErrorInfo`\-Methode ruft einen bestimmten Fehlertypinformationen ab.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## Siehe auch  
 [IDispError\-Schnittstelle](../../winscript/reference/idisperror-interface.md)
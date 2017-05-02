---
title: "IScriptEntry::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetName"
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::GetName
Für Einträge, die ein einzelnes Objekt darstellen \(wie eine Funktion\), den Namen des Objekts.  
  
## Syntax  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Den Namen des Objekts dargestellt durch den `IScriptEntry` Skriptblock.  Wenn ein Eintrag kein einzelnes Objekt darstellt, wird NULL zurückgegeben.  
  
 Untergeordnete Einträge stellen ein einzelnes Funktionsobjekt dar.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)
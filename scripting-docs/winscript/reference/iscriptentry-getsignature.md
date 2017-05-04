---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
Gibt Typinformationen für ein `IScriptEntry`\-Funktionsobjekt zurück.  
  
## Syntax  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### Parameter  
 `ppti`  
 \[out\] Typinformationen dieser zugeordnete `IScriptEntry`\-Funktionsobjekt.  
  
 `piMethod`  
 \[out\] Methodenindex im `ITypeInfo`\-Objekt.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Sie legen Typinformationen mithilfe von [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) oder von [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Typinformationen können durch den Eintrag auf Grundlage der interne Funktionsdarstellung auch generiert werden.  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)
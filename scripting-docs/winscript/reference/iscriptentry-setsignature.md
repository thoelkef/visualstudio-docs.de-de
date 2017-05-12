---
title: "IScriptEntry::SetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetSignature"
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetSignature
Legt Typinformationen für ein `IScriptEntry`\-Funktionsobjekt fest.  
  
## Syntax  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### Parameter  
 `pti`  
 \[in\] Die Typinformationen.  
  
 `iMethod`  
 \[in\] Der Methodenindex im `ITypeInfo`\-Objekt.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Sie legen Typinformationen mithilfe von `IScriptEntry::SetSignature` oder von [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Typinformationen können durch den Eintrag auf Grundlage der interne Funktionsdarstellung auch generiert werden.  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)
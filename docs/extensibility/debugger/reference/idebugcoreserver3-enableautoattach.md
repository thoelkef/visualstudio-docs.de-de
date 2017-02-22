---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Aktiviert das automatische Anhängen für die angegebenen Debugmodule.  
  
## Syntax  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### Parameter  
 `rgguidSpecificEngines`  
 \[in\]  Array von GUIDs für jedes Modul Debug\- zu kennzeichnen, z. B. AUTO\-anfügend.  
  
 `celtSpecificEngines`  
 \[in\]  Die Anzahl der Module angegeben in `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 \[in\]  Das beim Starten AUTO\-anfügen zu verwendende URL.  
  
 `pbstrSessionID`  
 \[out\]  ID der Sitzung, die AUTO\-angefügt wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  Ein Fehlercode ist `E_AUTO_ATTACH_NOT_REGISTERED`, der angibt, ob die selbstklebende Klassenfactory nicht registriert wurde.  
  
## Hinweise  
 Wenn ein Programm, das mit der angegebenen URL zugeordnet ist, gestartet wird, werden die angegebenen Debugmodule gestartet und automatisch angefügt.  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
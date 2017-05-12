---
title: "IScriptNode::GetLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetLanguage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetLanguage"
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IScriptNode::GetLanguage
Gibt die Skriptsprache zurück, die vom aktuellen Skripts\-Knoten verwendet wird.  
  
## Syntax  
  
```  
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Gibt "JScript" zurück, wenn der Skripts\-Knoten JScript verwendet, oder "VBScript", wenn der Skripts\-Knoten Visual Basic Scripting Edition \(VBScript\) verwendet.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)
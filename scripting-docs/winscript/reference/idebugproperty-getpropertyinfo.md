---
title: "IDebugProperty::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetPropertyInfo"
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetPropertyInfo
Ruft den Wert von `IDebugProperty` ab, der eine Methode oder eine indizierte Eigenschaft beschreibt.  
  
## Syntax  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGS dwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\] Gibt die `DBGPROP_INFO_FLAGS` Konstanten an, die die bestimmen die `DebugPropertyInfo`\-Struktur verwendet ausgefüllt werden Felder.  
  
 `nRadix`  
 \[in\] Wenn verwendet werden, Basis, alle numerischen Informationen formatiert werden.  
  
 `pPropertyInfo`  
 \[out\] Gibt die `DebugPropertyInfo`\-Struktur zurück, die die Eigenschaft beschreibt.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo\-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)
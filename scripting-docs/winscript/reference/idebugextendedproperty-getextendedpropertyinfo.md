---
title: "IDebugExtendedProperty::GetExtendedPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::GetExtendedPropertyInfo"
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::GetExtendedPropertyInfo
Ruft erweiterte Informationen für eine erweiterte Eigenschaft ab, die mehr Informationen als einfachere `IDebugProperty` ist.  
  
## Syntax  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### Parameter  
 `dwFieldSpec`  
 \[in\] Gibt die EX\_DBGPROP\_INFO\_FLAGS\-Konstanten an, die die bestimmen die `ExtendedDebugPropertyInfo`\-Struktur verwendet ausgefüllt werden Felder.  
  
 `nRadix`  
 \[in\] Wenn verwendet werden, Basis, alle numerischen Informationen interpretiert werden.  
  
 `pExtendedPropertyInfo`  
 \[out\] Gibt die `ExtendedDebugPropertyInfo`\-Struktur zurück, die die Eigenschaft beschreibt.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IDebugExtendedProperty\-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo\-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
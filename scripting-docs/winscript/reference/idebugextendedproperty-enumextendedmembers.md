---
title: "IDebugExtendedProperty::EnumExtendedMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.EnumExtendedMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::EnumExtendedMembers"
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::EnumExtendedMembers
Listet die Member einer erweiterten Eigenschaft auf.  
  
## Syntax  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### Parameter  
 `dwFieldSpec`  
 \[in\] Gibt die EX\_DBGPROP\_INFO\_FLAGS\-Konstanten an, die die Felder in den aufgelisteten erweiterten DebugEigenschaftenstruktur bestimmen, die gefüllt werden sollen.  
  
 `nRadix`  
 \[in\] Wenn verwendet werden, Basis, alle numerischen Informationen interpretiert werden.  
  
 `ppeepi`  
 \[out\] Gibt die `IEnumDebugExtendedPropertyInfo`\-Schnittstelle zurück, die die Membereigenschaften auflistet.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IDebugExtendedProperty\-Schnittstelle](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo\-Struktur](../../winscript/reference/extendeddebugpropertyinfo-structure.md)
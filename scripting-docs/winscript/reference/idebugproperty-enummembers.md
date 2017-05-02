---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
Listet die Member einer Eigenschaft auf.  
  
## Syntax  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Parameter  
 `dwFieldSpec`  
 \[in\] Gibt die `DBGPROP_INFO_FLAGS` Konstanten an, die bestimmen, welche Felder in den aufgelisteten DebugEigenschaftenstruktur gefüllt werden sollen.  
  
 `nRadix`  
 \[in\] Wenn verwendet werden, Basis, alle numerischen Informationen interpretiert werden.  
  
 `refiid`  
 \[in\] wird dieses IID zum Filtern des Enumerators übergeben.  Das IID ist eine der `IDebugPropertyEnumType`\-Schnittstellen, die von `IDebugPropertyEnumType_All` erben.  
  
 `ppEnum`  
 \[out\] Gibt die `IEnumDebugPropertyInfo`\-Schnittstelle zurück, die die Membereigenschaften auflistet.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType\_All\-Schnittstelle](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo\-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)
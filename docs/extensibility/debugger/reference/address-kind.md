---
title: "ADDRESS_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "ADDRESS_KIND-enumeration"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Arten von Adressen an.  
  
## Syntax  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```c#  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## Ausdrücke  
 ADDRESS\_KIND\_NATIVE  
 Eine systemeigene Adress\-, dargestellt durch die [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Struktur.  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 Eine nicht verwaltete Adresse relativ zu einem Zeiger `this` \(`Me` in Visual Basic\) und durch die [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur dargestellt.  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 Eine nicht verwaltete physikalische Adresse, dargestellt durch die [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur.  
  
 ADDRESS\_KIND\_METHOD  
 Eine Methode einer Klasse, dargestellt durch die [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Struktur.  
  
 ADDRESS\_KIND\_FIELD  
 Ein Feld einer Klasse, dargestellt durch die [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur.  
  
 ADDRESS\_KIND\_LOCAL  
 Die Adresse ist für eine lokale Variable und wird von der [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Struktur dargestellt.  
  
 ADDRESS\_KIND\_PARAM  
 Eine Methode oder ein Funktionsparameter, dargestellt durch die [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur.  
  
 ADDRESS\_KIND\_ARRAYELEM  
 Ein Arrayelement, dargestellt durch die [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Struktur.  
  
 ADDRESS\_KIND\_RETVAL  
 Ein Rückgabewert, dargestellt durch die [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Struktur.  
  
## Hinweise  
 Die [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)\-Methode gibt die [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die eine Union von möglichen Strukturen enthält, die [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur zurück.  Das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur enthält den Wert an `ADDRESS_KIND` und es wird beschrieben, wie Sie das Feld union interpretiert.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
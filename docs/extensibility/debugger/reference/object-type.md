---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "OBJECT_TYPE-enumeration"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Typ eines Objekts vom Ausdrucksauswertung an.  
  
## Syntax  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## Mitglieder  
 OBJECT\_TYPE\_BOOLEAN  
 Gibt an, dass das Objekt ein boolescher Wert ist.  
  
 OBJECT\_TYPE\_CHAR  
 Gibt an, dass das Objekt ein Zeichen ist.  
  
 OBJECT\_TYPE\_I1  
 Gibt an, dass das Objekt eine EinBYTE gesignierte Zahl ist.  
  
 OBJECT\_TYPE\_U1  
 Gibt an, dass das Objekt eine ganze Zahl EinBYTEs ohne Vorzeichen ist.  
  
 OBJECT\_TYPE\_I2  
 Gibt an, dass das Objekt eine 2\-Byte\-Ganzzahl mit Vorzeichen.  
  
 OBJECT\_TYPE\_U2  
 Gibt an, dass das Objekt eine 2\-Byte\-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT\_TYPE\_I4  
 Gibt an, dass das Objekt eine 4\-Byte\-Ganzzahl mit Vorzeichen.  
  
 OBJECT\_TYPE\_U4  
 Gibt an, dass das Objekt eine 4\-Byte\-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT\_TYPE\_I8  
 Gibt an, dass das Objekt eine 8\-Byte\-Ganzzahl mit Vorzeichen.  
  
 OBJECT\_TYPE\_U8  
 Gibt an, dass das Objekt eine 8\-Byte\-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT\_TYPE\_R4  
 Gibt an, dass das Objekt eine VierBYTE\-Gleitkommazahl ist.  
  
 OBJECT\_TYPE\_R8  
 Gibt an, dass das Objekt eine AchtBYTE\-Gleitkommazahl ist.  
  
 OBJECT\_TYPE\_OBJECT  
 Gibt an, dass es sich bei dem Objekt um ein Objekt handelt.  
  
 OBJECT\_TYPE\_NULL  
 Gibt an, dass das Objekt NULL ist.  
  
 OBJECT\_TYPE\_CLASS  
 Gibt an, dass das Objekt eine Klasse ist.  
  
## Hinweise  
 Übergabe als Argument an den [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) und [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)\-Methoden.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
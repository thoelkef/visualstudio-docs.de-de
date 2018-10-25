---
title: OBJECT_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c49036d66310be7774f3f8d36215aca4bedd7582
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922834"
---
# <a name="objecttype"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Typ eines Objekts von der ausdrucksauswertung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_OBJECT_TYPE {   
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
  
```csharp  
public enum enum_OBJECT_TYPE {   
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
  
## <a name="members"></a>Member  
 OBJECT_TYPE_BOOLEAN  
 Gibt an, dass das Objekt ein boolescher Wert.  
  
 OBJECT_TYPE_CHAR  
 Gibt an, dass das Objekt ein Zeichen ist.  
  
 OBJECT_TYPE_I1  
 Gibt an, dass das Objekt eine ein-Byte-Ganzzahl mit Vorzeichen ist.  
  
 OBJECT_TYPE_U1  
 Gibt an, dass das Objekt eine ein-Byte-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT_TYPE_I2  
 Gibt an, dass das Objekt eine 2-Byte-Ganzzahl mit Vorzeichen ist.  
  
 OBJECT_TYPE_U2  
 Gibt an, dass das Objekt eine 2-Byte-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT_TYPE_I4  
 Gibt an, dass das Objekt eine vier-Byte-Ganzzahl mit Vorzeichen ist.  
  
 OBJECT_TYPE_U4  
 Gibt an, dass das Objekt eine vier-Byte-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT_TYPE_I8  
 Gibt an, dass das Objekt eine 8-Byte-Ganzzahl mit Vorzeichen ist.  
  
 OBJECT_TYPE_U8  
 Gibt an, dass das Objekt eine 8-Byte-Ganzzahl ohne Vorzeichen ist.  
  
 OBJECT_TYPE_R4  
 Gibt an, dass das Objekt eine vier-Byte-Gleitkommazahl.  
  
 OBJECT_TYPE_R8  
 Gibt an, dass das Objekt eine 8-Byte-Gleitkommazahl.  
  
 OBJECT_TYPE_OBJECT  
 Gibt an, dass das Objekt ein Objekt.  
  
 OBJECT_TYPE_NULL  
 Gibt an, dass das Objekt NULL ist.  
  
 OBJECT_TYPE_CLASS  
 Gibt an, dass das Objekt einer Klasse ist.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) und [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)


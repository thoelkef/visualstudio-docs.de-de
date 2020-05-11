---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714133"
---
# <a name="object_type"></a>Object_Type
Gibt den Typ eines Objekts aus dem Ausdrucksauswertungswert an.

## <a name="syntax"></a>Syntax

```cpp
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

```csharp
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

## <a name="fields"></a>Felder
 `OBJECT_TYPE_BOOLEAN`\
 Gibt an, dass es sich bei dem Objekt um ein boolesche Objekt handelt.

 `OBJECT_TYPE_CHAR`\
 Gibt an, dass es sich bei dem Objekt um ein Zeichen handelt.

 `OBJECT_TYPE_I1`\
 Gibt an, dass es sich bei dem Objekt um eine einbyte signierte Ganzzahl handelt.

 `OBJECT_TYPE_U1`\
 Gibt an, dass es sich bei dem Objekt um eine ganzzahlige Ganzzahl ohne Durchtbyte handelt.

 `OBJECT_TYPE_I2`\
 Gibt an, dass es sich bei dem Objekt um eine zweibytsignierte Ganzzahl handelt.

 `OBJECT_TYPE_U2`\
 Gibt an, dass es sich bei dem Objekt um eine ganzzahlige Ganzzahl mit zwei Byte handelt.

 `OBJECT_TYPE_I4`\
 Gibt an, dass es sich bei dem Objekt um eine vierbyte signierte Ganzzahl handelt.

 `OBJECT_TYPE_U4`\
 Gibt an, dass es sich bei dem Objekt um eine ganzzahlige Vier-Byte-Datei ohne Vorzeichen handelt.

 `OBJECT_TYPE_I8`\
 Gibt an, dass es sich bei dem Objekt um eine acht byte signierte Ganzzahl handelt.

 `OBJECT_TYPE_U8`\
 Gibt an, dass es sich bei dem Objekt um eine ganzzahlige Achtbyte ohne Vorzeichen handelt.

 `OBJECT_TYPE_R4`\
 Gibt an, dass es sich bei dem Objekt um eine Gleitkommazahl mit vier Byte handelt.

 `OBJECT_TYPE_R8`\
 Gibt an, dass es sich bei dem Objekt um eine Gleitkommazahl mit acht Byte handelt.

 `OBJECT_TYPE_OBJECT`\
 Gibt an, dass es sich bei dem Objekt um ein Objekt handelt.

 `OBJECT_TYPE_NULL`\
 Gibt an, dass das Objekt NULL ist.

 `OBJECT_TYPE_CLASS`\
 Gibt an, dass es sich bei dem Objekt um eine Klasse handelt.

## <a name="remarks"></a>Bemerkungen
 Übergeben als Argument an die [Methoden CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) und [CreateArrayObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

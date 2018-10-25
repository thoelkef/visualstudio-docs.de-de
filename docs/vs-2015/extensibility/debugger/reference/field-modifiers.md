---
title: FIELD_MODIFIERS | Microsoft-Dokumentation
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
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f70314c10928f3f81ab19d09f28585d8e924be3d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922990"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Modifizierer für ein Feld an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Member  
 FIELD_MOD_ACCESS_TYPE  
 Gibt an, dass das Feld nicht zugegriffen werden kann.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Gibt an, dass das Feld über öffentlichen Zugriff hat.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Gibt an, dass das Feld Zugriff geschützt ist.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Gibt an, dass das Feld privaten Zugriff hat.  
  
 FIELD_MOD_NOMODIFIERS  
 Gibt an, dass das Feld keine Modifizierer verfügt.  
  
 FIELD_MOD_STATIC  
 Gibt an, dass das Feld statisch ist.  
  
 FIELD_MOD_CONSTANT  
 Gibt an, dass das Feld eine Konstante ist.  
  
 FIELD_MOD_TRANSIENT  
 Gibt an, dass das Feld vorübergehend ist.  
  
 FIELD_MOD_VOLATILE  
 Gibt an, dass das Feld "volatile" ist.  
  
 FIELD_MOD_ABSTRACT  
 Gibt an, dass das Feld abstrakt ist.  
  
 FIELD_MOD_NATIVE  
 Gibt an, dass das Feld native.  
  
 FIELD_MOD_SYNCHRONIZED  
 Gibt an, dass das Feld synchronisiert wird.  
  
 FIELD_MOD_VIRTUAL  
 Gibt an, dass das Feld virtuell ist.  
  
 FIELD_MOD_INTERFACE  
 Gibt an, dass das Feld eine Schnittstelle.  
  
 FIELD_MOD_FINAL  
 Gibt an, dass das Feld Ihrem endgültigen Zustand vorliegt.  
  
 FIELD_MOD_SENTINEL  
 Gibt an, dass das Feld Sentinel.  
  
 FIELD_MOD_INNERCLASS  
 Gibt an, dass das Feld einer inneren Klasse.  
  
 FIELD_TYPE_OPTIONAL  
 Gibt an, dass das Feld optional ist.  
  
 FIELD_MOD_BYREF  
 Gibt an, dass das Feld mit einem Verweisargument ist. Dies ist insbesondere für Methodenargumente.  
  
 FIELD_MOD_HIDDEN  
 Gibt an, dass das Feld in einem anderen Kontext angezeigt oder ausgeblendet werden muss. z. B. [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] statischen lokalen Variablen.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Gibt an, dass das Feld repräsentiert den ein Objekt mit einer `IUnknown` Schnittstelle.  
  
 FIELD_MOD_SPECIAL_NAME  
 Gibt an, dass das Feld einen speziellen Namen, z. B. `.ctor` für einen Konstruktor ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nur).  
  
 FIELD_MOD_HIDEBYSIG  
 Gibt an, dass das Feld enthält den `Overloads` Schlüsselwort angewendet wird ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nur).  
  
 FIELD_MOD_WRITEONLY  
 Gibt an, dass das Feld schreibgeschützt ist. Dieser Wert befindet sich nicht im `FIELD_MOD_ALL`, da nur mit diesen Feldern nur Schreibzugriff für die funktionsauswertung ist. Ein Benutzer muss explizit anfordern `FIELD_MOD_WRITEONLY` Felder.  
  
 FIELD_MOD_ACCESS_MASK  
 Gibt eine Maske für den Feldzugriff an.  
  
 FIELD_MOD_MASK  
 Gibt eine Maske für feldmodifizierern an.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `dwModifiers` Mitglied der [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.  
  
 Diese Werte werden auch zum Übergeben der [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) Methode zum Filtern nach bestimmten Feldern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)


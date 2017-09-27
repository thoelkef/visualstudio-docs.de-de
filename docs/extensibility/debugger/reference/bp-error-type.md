---
title: BP_ERROR_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: ab0dc686c4d002733bf8501be042e33c500fb8e3
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Gibt den Fehlertyp eines Haltepunkts an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 BPET_NONE  
 Gibt kein Haltepunkt Fehler an.  
  
 BPET_TYPE_WARNING  
 Gibt eine Warnung-Stil Haltepunkt Fehler an.  
  
 BPET_TYPE_ERROR  
 Gibt Fehler Haltepunkt Error-Format an.  
  
 BPET_SEV_HIGH  
 Gibt einen hohen Schweregrad Haltepunkt-Fehler.  
  
 BPET_SEV_GENERAL  
 Gibt ein mittlerer Schweregrad Haltepunkt Fehler an.  
  
 BPET_SEV_LOW  
 Gibt einen Fehler mit niedriger Schweregrad Haltepunkt an.  
  
 BPET_TYPE_MASK  
 Gibt eine Maske-Stil Haltepunkt Fehler an.  
  
 BPET_SEV_MASK  
 Gibt einen Haltepunkt Schweregrad-Maske-Style '-Fehler.  
  
 BPET_GENERAL_WARNING  
 Gibt einen Haltepunkt Allgemein-Warnung-Style '-Fehler.  
  
 BPET_GENERAL_ERROR  
 Gibt einen Haltepunkt Allgemein-Fehler-Style '-Fehler.  
  
 BPET_ALL  
 Gibt alle Haltepunkt Fehlertypen an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR` und verwendet für die `dwType` Mitglied der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur. Übergeben als Parameter an die [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) Methode.  
  
 Ein Haltepunkt Fehlertyp besteht aus einem Typ und Schweregrad. Dies bedeutet, dass ein Haltepunkt Fehlertyp nie nur ein Typ ist (z. B. `BPET_TYPE_ERROR`,) oder mit einem Schweregrad (z. B. `BPET_SEV_GENERAL`) selbst. `BPET_GENERAL_WARNING`und `BPET_GENERAL_ERROR` Geben Sie vordefinierte Werte für allgemeine Warnungs- und Haltepunkte.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

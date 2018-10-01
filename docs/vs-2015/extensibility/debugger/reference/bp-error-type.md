---
title: BP_ERROR_TYPE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 574830c7875b0711d6e14aa5b09370a5bf217903
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520562"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BP_ERROR_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-error-type).  
  
Gibt den Fehlertyp eines Haltepunkts an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Gibt keine haltepunktfehler an.  
  
 BPET_TYPE_WARNING  
 Gibt eine Warnung-Stil haltepunktfehler an.  
  
 BPET_TYPE_ERROR  
 Gibt Fehler Haltepunkt Error-Format an.  
  
 BPET_SEV_HIGH  
 Gibt einen mit hohem Schweregrad haltepunktfehler an.  
  
 BPET_SEV_GENERAL  
 Gibt einen mit mittleren Schweregrad haltepunktfehler an.  
  
 BPET_SEV_LOW  
 Gibt einen haltepunktfehler mit niedriger Schweregrad an.  
  
 BPET_TYPE_MASK  
 Gibt eine Maske-Stil haltepunktfehler an.  
  
 BPET_SEV_MASK  
 Gibt einen haltepunktfehler für Schweregrad-Maske-Style.  
  
 BPET_GENERAL_WARNING  
 Gibt einen für allgemeine-Warnung-Style-haltepunktfehler.  
  
 BPET_GENERAL_ERROR  
 Gibt eine allgemeine-Error-Format haltepunktfehler an.  
  
 BPET_ALL  
 Gibt alle Haltepunkttypen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR` und wird verwendet, für die `dwType` Mitglied der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur. Übergeben als Parameter an die [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) Methode.  
  
 Eine Haltepunkt-Fehlertyp besteht aus einem Typ und einen Schweregrad aus. Dies bedeutet, dass ein Fehler Haltepunkt niemals nur ein Typ ist (z. B. `BPET_TYPE_ERROR`,) oder einen Schweregrad (z. B. `BPET_SEV_GENERAL`) selbst. `BPET_GENERAL_WARNING` und `BPET_GENERAL_ERROR` Geben Sie vordefinierte Werte für allgemeine Warnungs- und Haltepunkte.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)


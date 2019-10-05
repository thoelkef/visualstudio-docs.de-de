---
title: BP_LOCATION_CODE_STRING | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50c48098aee3b1077edec99210e7ab624d2a8d6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153465"
---
# <a name="bplocationcodestring"></a>BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Verwendet zum Festlegen von Code Breakpoints, die basierend auf einer Zeichenfolge, die der Benutzer aus der integrierten Entwicklungsumgebung (IDE) eingeben können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>Member  
 `bstrContext`  
 Der Kontext der der Haltepunkt im Code, in der Regel eine Methode oder Funktion Namen wie für eine Aufrufliste.  
  
 `bstrCodeExpr`  
 Die Zeichenfolge, der in der Benutzer eingibt, um die codehaltepunkt zu beschreiben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)

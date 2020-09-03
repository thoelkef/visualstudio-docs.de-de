---
title: BP_COND_STYLE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2674381992bd86f0144af103615f0a3922fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153571"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Haltepunkt-Bedingungs Stil für ausstehende und gebundene Haltepunkte an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Member  
 BP_COND_NONE  
 Löst den Haltepunkt aus, wenn die Position des Breakpoints erreicht ist. Es wurde keine breakpointbedingung angegeben.  
  
 BP_COND_WHEN_TRUE  
 Löst den Haltepunkt nur aus, wenn der bedingte Ausdruck, der dem Breakpoint zugeordnet ist, zu ausgewertet wird `true` .  
  
 BP_COND_WHEN_CHANGED  
 Löst den Breakpoint nur aus, wenn sich der Wert des bedingten Ausdrucks, der dem Breakpoint zugeordnet ist, von der vorherigen Auswertung geändert hat.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird für den `styleCondition` Member der [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Struktur verwendet.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)

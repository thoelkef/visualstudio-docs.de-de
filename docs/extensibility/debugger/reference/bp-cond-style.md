---
title: BP_COND_STYLE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b3d7bd22633985973975cb54d54ab3eb0837e30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Gibt den Haltepunkt Bedingung Stil für ausstehende und Haltepunkte gebunden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Member  
 BP_COND_NONE  
 Wird den Haltepunkt ausgelöst, wenn Position der Haltepunkt erreicht wird. Keine Bedingung für Haltepunkt angegeben.  
  
 BP_COND_WHEN_TRUE  
 Den Haltepunkt ausgelöst wird, nur wenn der bedingte Ausdruck mit dem Haltepunkt zugeordnete ergibt `true`.  
  
 BP_COND_WHEN_CHANGED  
 Wird ausgelöst, die der Breakpoint nur, wenn der Wert des bedingten Ausdrucks mit dem Haltepunkt zugeordneten aus der vorherigen Bewertung geändert hat.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `styleCondition` Mitglied der [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
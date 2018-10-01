---
title: BP_COND_STYLE | Microsoft-Dokumentation
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
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5e0df33ef462d6b1b8bbe013f30baab894ea82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511003"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BP_COND_STYLE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-cond-style).  
  
Gibt den Haltepunkt-Bedingung-Stil für ausstehende und gebundene Haltepunkte.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Löst den Haltepunkt an, bei des Haltepunkts Position erreichen. Keine Bedingung für Haltepunkt angegeben.  
  
 BP_COND_WHEN_TRUE  
 Den Haltepunkt ausgelöst wird, nur wenn der bedingte Ausdruck mit dem Haltepunkt verknüpften ergibt `true`.  
  
 BP_COND_WHEN_CHANGED  
 Wird ausgelöst, die der Haltepunkt nur, wenn der Wert des bedingten Ausdrucks mit dem Haltepunkt zugeordneten aus der vorherigen Auswertung geändert wurde.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `styleCondition` Mitglied der [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)


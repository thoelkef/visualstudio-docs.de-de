---
title: IDebugProperty-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>IDebugProperty-Schnittstelle
Verwendet, um eine hierarchische Eigenschaft der Entität, der debuggt wird beschreiben, die über einen Namen, Typ und Wert verfügt. In den meisten Fällen `IDebugProperty` wird verwendet, um das Ergebnis der Auswertung von Ausdrücken, Auswertung der Anweisung oder Register Evaluation beschrieben.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProperty` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Abrufen der `DebugPropertyInfo` , die eine Beschreibung`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Ruft die erweiterten Informationen für eine Eigenschaft ab.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Listet die Elemente einer Eigenschaft an.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Ruft das übergeordnete Element einer Eigenschaft ab.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: dbgprop.h
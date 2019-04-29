---
title: IDebugProperty-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 963b11a4760fad8086822f13db129fae76467802
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979061"
---
# <a name="idebugproperty-interface"></a>IDebugProperty-Schnittstelle
Wird verwendet, um eine hierarchische Eigenschaft der Entität im Debugmodus befindlichen beschreiben, die über einen Namen, Typ und Wert verfügt. In den meisten Fällen `IDebugProperty` wird verwendet, um das Ergebnis der Auswertung von Ausdrücken, Auswertung der Anweisung oder Register Evaluation beschreiben.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProperty` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Abrufen der `DebugPropertyInfo` , die zeigt, wie diese `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Ruft den erweiterten Informationen für eine Eigenschaft ab.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Listet die Member einer Eigenschaft.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Ruft das übergeordnete Element eine Eigenschaft ab.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: dbgprop.h
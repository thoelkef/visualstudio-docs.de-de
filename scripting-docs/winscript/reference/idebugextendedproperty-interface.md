---
title: Idebugextendecodproperty-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedProperty interface
ms.assetid: e92ea064-0d92-44cf-bb9f-abda783d84be
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24a93cb3bd230e2489b58d78f6d414ba1df006ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572493"
---
# <a name="idebugextendedproperty-interface"></a>IDebugExtendedProperty-Schnittstelle
Erweitert `IDebugProperty`-Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden, die von `IDebugProperty` geerbt werden, stellt diese Schnittstelle die folgenden Methoden zur Verfügung.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|Ruft das `ExtendedDebugPropertyInfo` ab, das diese beschreibt `IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|Listet die Member einer erweiterten Eigenschaft auf.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: dbgprop. h  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)
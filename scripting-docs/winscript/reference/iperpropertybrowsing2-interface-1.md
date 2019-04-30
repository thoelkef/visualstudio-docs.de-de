---
title: IPerPropertyBrowsing2-Schnittstelle 1 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944902"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2-Schnittstelle 1
Greift auf können die Informationen in den Eigenschaftenseiten von ein-Objekt bereitgestellt werden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|`GetDisplayString`|Gibt eine Textzeichenfolge, die Beschreibung der angegebenen Eigenschaft zurück.|  
|`MapPropertyToPage`|Gibt die CLSID der Eigenschaftenseite, die ermöglicht die Bearbeitung der angegebenen Eigenschaft zurück.|  
|`GetPredefinedStrings`|Gibt ein gezähltes Array von Zeichenfolgen (`LPOLESTR` Zeiger) Auflisten von den Beschreibungen der zulässigen Werte, die die angegebene Eigenschaft annehmen kann.|  
|`SetPredefinedValue`|Legt den Wert der Eigenschaft auf die vordefinierten Wert, der durch das Token identifiziert wird. `dwCookie.`|  
  
## <a name="requirements"></a>Anforderungen  
 Header: dbgprop.h
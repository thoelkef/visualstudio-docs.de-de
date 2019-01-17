---
title: IPerPropertyBrowsing2-Schnittstelle 1 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344028"
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
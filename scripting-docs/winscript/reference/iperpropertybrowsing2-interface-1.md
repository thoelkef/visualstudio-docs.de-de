---
title: IPerPropertyBrowsing2-Schnittstelle 1 | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2-Schnittstelle 1
Greift auf angeboten die Informationen in den Eigenschaftenseiten von einem Objekt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|`GetDisplayString`|Gibt eine Textzeichenfolge, die die angegebene Eigenschaft beschreibt.|  
|`MapPropertyToPage`|Gibt die CLSID der Eigenschaftenseite, die ermöglicht Manipulation der angegebenen Eigenschaft zurück.|  
|`GetPredefinedStrings`|Gibt ein gezähltes Array von Zeichenfolgen (`LPOLESTR` Zeiger) Auflisten der Beschreibungen der zulässigen Werte, die die angegebene Eigenschaft annehmen kann.|  
|`SetPredefinedValue`|Legt den Wert der Eigenschaft auf den vordefinierten Wert identifiziert, von dem token`dwCookie.`|  
  
## <a name="requirements"></a>Anforderungen  
 Header: dbgprop.h
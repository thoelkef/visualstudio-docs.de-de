---
title: IDebugFormatter-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35d1b811a017895ca40f3325bd0ac456070184f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979226"
---
# <a name="idebugformatter-interface"></a>IDebugFormatter-Schnittstelle
Ermöglicht, dass eine Sprache oder IDE den Wechsel zwischen VARIANT-Werten oder VARTYPE-Typen und -Zeichenfolgen anpasst.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugFormatter` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Gibt eine Zeichenfolge, die den angegebenen VARIANT-Wert darstellt.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Gibt eine Variante, die die angegebene Zeichenfolge enthält.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Gibt eine Zeichenfolge, die den angegebenen VARTYPE-Wert darstellt.|
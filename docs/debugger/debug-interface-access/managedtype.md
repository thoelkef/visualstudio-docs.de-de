---
title: ManagedType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagManagedType symbol
- managed type symbol
- ManagedType symbol
ms.assetid: 5db99e2a-4f2e-4796-89b7-b401b151826f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 486739ae466431397e514d3248857fc606a74d6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888243"
---
# <a name="managedtype"></a>ManagedType
Ein verwalteter Typ (einem Symbol, definiert durch die Metadaten oder Native für die Speicher- und Verwaltungsfunktionen von Sprachen wie z. B. C#) wird durch identifiziert eine `SymTagManagedType` Symbol.  
  
## <a name="properties"></a>Eigenschaften  
 Die folgende Tabelle zeigt zusätzliche gültige Eigenschaften für diesen Symboltyp.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Name des verwalteten Symbols.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagManagedType` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|  
  
## <a name="see-also"></a>Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
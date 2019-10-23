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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bf61dce9940279b490d9270420cc45baf0b82dc0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738653"
---
# <a name="managedtype"></a>ManagedType
Ein verwalteter Typ (ein beliebiges Symbol, das durch Metadaten definiert ist, oder System eigen für die Speicher- C#und Ressourcen Verwaltungsfunktionen von Sprachen wie) wird durch ein `SymTagManagedType` Symbol gekennzeichnet.

## <a name="properties"></a>Eigenschaften
 In der folgenden Tabelle sind zusätzliche gültige Eigenschaften für diesen Symboltyp aufgeführt.

|property|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Der Name des verwalteten Symbols.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagManagedType` zurück (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte).|

## <a name="see-also"></a>Siehe auch
- [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
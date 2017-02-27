---
title: "ManagedType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagManagedType-Symbol"
  - "Verwaltetes Typsymbol"
  - "ManagedType-Symbol"
ms.assetid: 5db99e2a-4f2e-4796-89b7-b401b151826f
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ManagedType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein verwalteter Typ \(ein Symbol definiert von Metadaten oder dem systemeigenen Betriebsmittelverwaltungs von Arbeitsspeicher und zur Funktionalität von Sprachen wie C\#\) wird durch ein `SymTagManagedType` Symbol identifiziert.  
  
## Eigenschaften  
 In der folgenden Tabelle sind die zusätzlichen gültige Eigenschaften für diesen Typ Symbol an.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Name des verwalteten Symbols.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagManagedType` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Siehe auch  
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
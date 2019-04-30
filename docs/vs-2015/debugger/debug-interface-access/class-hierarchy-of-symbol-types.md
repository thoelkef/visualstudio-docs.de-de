---
title: Klassenhierarchie der Symboltypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a7b3edb0262e3e2b4f0cde51b499e25b04aba51
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442912"
---
# <a name="class-hierarchy-of-symbol-types"></a>Klassenhierarchie der Symboltypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die folgende Tabelle beschreibt die Symboltypen in der Klassenhierarchie.  
  
## <a name="symbol-types"></a>Symboltypen  
  
|Symboltyp|Beschreibung|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol zur Darstellung von jeder Klasse, Struktur und Union.|  
|[Enum (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol für Enumerationstypen.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol für Zeigertypen.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol für Arraytypen.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol für Basistypen|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, die Namen für andere Typen eingeführt werden.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbol für jede Basisklasse eines benutzerdefinierten Typs (UDT) verwendet.|  
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol für Friend-Klassen und Friend-Funktionen.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol für jede eindeutige Signatur.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol für jeden Parameter einer Funktion.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbol für die Größe der virtuellen Tabelle.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol für eine virtuelle Tabelle.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol für vom Hersteller festgelegten Typ.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol für einen Typ in den Metadaten definiert.|  
|[Dimension](../../debugger/debug-interface-access/dimension.md)|Symbol für die Dimensionen des Arrays.|  
  
> [!NOTE]
> Jedes Symbol kann über Eigenschaften verfügen, die Informationen über das Symbol als auch Verweise auf andere Symbole enthalten. Diese Eigenschaften werden in den einzelnen Symbol-Themen aufgelistet.  
  
## <a name="see-also"></a>Siehe auch  
 [CV_access_e-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)

---
title: "Klassenhierarchie der Symboltypen | Microsoft Docs"
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
  - "Symbole [DIA-SDK], Klassenhierarchien"
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Klassenhierarchie der Symboltypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der folgenden Tabelle werden die Typen von Symbolen in der Klassenhierarchie.  
  
## Symbol\-Typen  
  
|Symbol "|Beschreibung|  
|--------------|------------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbol verwendet, um jede Klasse, Struktur und Union darzustellen.|  
|[Enum \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbol für Enumerationstypen.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbol für Zeigertypen.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbol für Arraytypen.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbol für Basistypen|  
|[Typedef \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbol, das Namen für andere Typen vorstellt.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbol für jede Basisklasse benutzerdefinierter Typ \(UDT\).|  
|[Friend \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol für friend\-Klassen und Friend\-Funktionen.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol für jede eindeutige Funktionssignatur.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol für jeden Parameter einer Funktion.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbol für die Größe der virtuellen Tabelle.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbol für eine virtuelle Tabelle.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbol für Anbieter\-definierten Typ.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbol für einen Typ in den Metadaten definiert.|  
|[Dimension](../../debugger/debug-interface-access/dimension.md)|Symbol für Arraydimensionen.|  
  
> [!NOTE]
>  Jedes Symbol kann Eigenschaften, die Informationen über das Symbol speichern, sowie Verweise auf andere Symbole verfügen.  Diese Eigenschaften werden in den einzelnen Themen Symbole aufgelistet.  
  
## Siehe auch  
 [CV\_access\_e\-Enumeration](../../debugger/debug-interface-access/cv-access-e.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
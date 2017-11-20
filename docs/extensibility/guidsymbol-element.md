---
title: GuidSymbol Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcad9882b1c72c15837529d736eeabff58f3826
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="guidsymbol-element"></a>GuidSymbol-Element
Die `GuidSymbol` Element enthält die GUID des GUID: ID-Paar, das ein Menü, eine Gruppe oder ein Befehl darstellt. Die ID stammen aus einer `IDSymbol` Element in der `GuidSymbol` Element. Die `GuidSymbol` Element verfügt über eine `name` -Attribut, das einen Anzeigenamen für die GUID der in enthalten ist, bietet die `value` Attribut.  
  
## <a name="syntax"></a>Syntax  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Name|Erforderlich. Der Name des Symbols GUID.|  
|Wert|Erforderlich. GUID der GUID-Symbol.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[IDSymbol-Element](../extensibility/idsymbol-element.md)|Enthält die ID der dem GUID: ID-Paar, die ein Menü, eine Gruppe oder ein Befehl darstellt.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Symbols-Element](../extensibility/symbols-element.md)|Gruppen `GuidSymbol` Elemente in einer VSCT-Datei.|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel eine VSCT-Datei enthält drei `GuidSymbol` Elemente in seiner `Symbols` Abschnitt, für das Paket selbst eine für den Befehlssatz (die Auflistung von Menüs, Gruppen und Befehle, die das Paket zur Verfügung gestellt) und eine für die Bitmaps, die bereitstellen Symbole für Schaltflächen und andere visuellen Komponenten. Jede `IDSymbol` Element in einer bestimmten `GuidSymbol` -Element muss einen eindeutigen aufweisen `value`. Allerdings `IDSymbol` Elemente, die identische Werte haben können in einem Paket vorhanden, solange sie anderen übergeordneten Objekte verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
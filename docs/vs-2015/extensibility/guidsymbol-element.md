---
title: Guidsymbol-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204220"
---
# <a name="guidsymbol-element"></a>GuidSymbol-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das- `GuidSymbol` Element enthält die GUID des GUID: ID-Paars, das ein Menü, eine Gruppe oder einen Befehl darstellt. Die ID stammt von einem `IDSymbol` Element im- `GuidSymbol` Element. Das- `GuidSymbol` Element verfügt über ein- `name` Attribut, das einen anzeigen Amen für die GUID bereitstellt, die im-Attribut enthalten ist `value` .  
  
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
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|name|Erforderlich. Der Name des GUID-Symbols.|  
|value|Erforderlich. GUID des GUID-Symbols.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[IDSymbol-Element](../extensibility/idsymbol-element.md)|Enthält die ID des GUID: ID-Paars, das ein Menü, eine Gruppe oder einen Befehl darstellt.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[Symbols-Element](../extensibility/symbols-element.md)|Gruppiert `GuidSymbol` Elemente in einer vsct-Datei.|  
  
## <a name="remarks"></a>Bemerkungen  
 In der Regel enthält eine vsct-Datei drei `GuidSymbol` Elemente in Ihrem `Symbols` Abschnitt, eine für das Paket selbst, eine für den Befehlssatz (die Auflistung der Menüs, Gruppen und Befehle, die das Paket verfügbar macht) und eine für die Bitmaps, die Symbole für Schaltflächen und andere visuelle Komponenten bereitstellen. Jedes `IDSymbol` Element in einem bestimmten `GuidSymbol` Element muss über einen eindeutigen verfügen `value` . Allerdings `IDSymbol` können Elemente mit identischen Werten in einem Paket vorhanden sein, solange Sie über unterschiedliche übergeordnete Elemente verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

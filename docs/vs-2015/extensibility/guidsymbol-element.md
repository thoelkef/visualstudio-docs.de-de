---
title: GuidSymbol-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e6e5bab37e9a0b9f0ffdf03778532d9657539c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515136"
---
# <a name="guidsymbol-element"></a>GuidSymbol-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [GuidSymbol-Element](https://docs.microsoft.com/visualstudio/extensibility/guidsymbol-element).  
  
Die `GuidSymbol` Element enthält die GUID des das GUID: ID-Paar, das ein Menü, Gruppe oder den Befehl darstellt. Die ID stammt aus einer `IDSymbol` Element in der `GuidSymbol` Element. Die `GuidSymbol` Element verfügt über eine `name` -Attribut, das einen Anzeigenamen für die GUID, der in enthalten ist, enthält die `value` Attribut.  
  
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
|Name|Erforderlich. Der Name des dem GUID-Symbol.|  
|Wert|Erforderlich. GUID der GUID-Symbol.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[IDSymbol-Element](../extensibility/idsymbol-element.md)|Enthält die ID der dem GUID: ID-Paar, die ein Menü, Gruppe oder den Befehl darstellt.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Symbols-Element](../extensibility/symbols-element.md)|Gruppen `GuidSymbol` Elemente in einer VSCT-Datei.|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel eine VSCT-Datei enthält drei `GuidSymbol` Elemente in der `Symbols` Abschnitt, für das Paket selbst, für den Befehlssatz (die Sammlung von Menüs, Gruppen und Befehle, die das Paket zur Verfügung stellt) und eine für die Bitmaps, die bereitstellen Symbole für Schaltflächen und anderen visuellen Komponenten. Jede `IDSymbol` Element in einer angegebenen `GuidSymbol` -Element muss einen eindeutigen besitzen `value`. Allerdings `IDSymbol` Elemente, die identische Werte aufweisen können in einem Paket vorhanden, solange sie die verschiedene übergeordneten Elementen verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)


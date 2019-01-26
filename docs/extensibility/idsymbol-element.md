---
title: IDSymbol-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93973eeadf7629201aa6bd739f33a094677efe5f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961477"
---
# <a name="idsymbol-element"></a>IDSymbol-element
Die `IDSymbol` Element enthält die ID der dem GUID: ID-Paar, ein Menü, Gruppe oder den Befehl darstellt. Die GUID wird von der übergeordneten `GuidSymbol` Element. Die `IDSymbol` Element verfügt über eine `name` -Attribut, das einen Anzeigenamen für die ID, der in enthalten ist, enthält die `value` Attribut.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Name|Erforderlich. Der Name des ID-Symbols.|  
|Wert|Erforderlich. Numerische ID-Wert des ID-Symbols.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[GuidSymbol-element](../extensibility/guidsymbol-element.md)|Enthält die GUID, der das GUID: ID-Paar, die ein Menü, Gruppe oder den Befehl darstellt. Gruppiert `IDSymbol`-Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 Jede `IDSymbol` Element in einer angegebenen `GuidSymbol` -Element muss einen eindeutigen besitzen `value`. Allerdings `IDSymbol` Elemente, die identische Werte aufweisen können in einem Paket vorhanden, solange sie die verschiedene übergeordneten Elementen verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
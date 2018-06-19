---
title: IDSymbol Element | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71979bd4f859257555c9d72ac5521a5ae21b9ed4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127525"
---
# <a name="idsymbol-element"></a>IDSymbol-Element
Die `IDSymbol` Element enthält die ID der dem GUID: ID-Paar, ein Menü, eine Gruppe oder ein Befehl darstellt. Die GUID stammt aus dem übergeordneten `GuidSymbol` Element. Die `IDSymbol` Element verfügt über eine `name` -Attribut, das einen Anzeigenamen für die ID der in enthalten ist, bietet die `value` Attribut.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|[GuidSymbol-Element](../extensibility/guidsymbol-element.md)|Enthält die GUID des GUID: ID-Paar, die ein Menü, eine Gruppe oder ein Befehl darstellt. Gruppiert `IDSymbol`-Elemente.|  
  
## <a name="remarks"></a>Hinweise  
 Jede `IDSymbol` Element in einer bestimmten `GuidSymbol` -Element muss einen eindeutigen aufweisen `value`. Allerdings `IDSymbol` Elemente, die identische Werte haben können in einem Paket vorhanden, solange sie anderen übergeordneten Objekte verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
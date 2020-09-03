---
title: Idsymbol-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4e686b5e105b0ea0aa80783137093679d4cad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203968"
---
# <a name="idsymbol-element"></a>IDSymbol-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das- `IDSymbol` Element enthält die ID des GUID: ID-Paars, das ein Menü, eine Gruppe oder einen Befehl darstellt. Die GUID stammt aus dem übergeordneten `GuidSymbol` Element. Das- `IDSymbol` Element verfügt über ein- `name` Attribut, das einen anzeigen Amen für die ID bereitstellt, die im-Attribut enthalten ist `value` .  
  
## <a name="syntax"></a>Syntax  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|name|Erforderlich. Name des ID-Symbols.|  
|value|Erforderlich. Numerischer ID-Wert des ID-Symbols.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[GuidSymbol-Element](../extensibility/guidsymbol-element.md)|Enthält die GUID des GUID: ID-Paars, das ein Menü, eine Gruppe oder einen Befehl darstellt. Gruppiert `IDSymbol`-Elemente.|  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes `IDSymbol` Element in einem bestimmten `GuidSymbol` Element muss über einen eindeutigen verfügen `value` . Allerdings `IDSymbol` können Elemente mit identischen Werten in einem Paket vorhanden sein, solange Sie über unterschiedliche übergeordnete Elemente verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

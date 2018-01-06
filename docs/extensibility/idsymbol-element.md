---
title: IDSymbol Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 004b40acb50fe85604d0a3cfa9f5626891fa66a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
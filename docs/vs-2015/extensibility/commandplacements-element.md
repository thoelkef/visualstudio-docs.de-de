---
title: CommandPlacements-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 449a419a84f0f367ea1c97ec56d57fcd936ae423
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510481"
---
# <a name="commandplacements-element"></a>CommandPlacements-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CommandPlacements-Element](https://docs.microsoft.com/visualstudio/extensibility/commandplacements-element).  
  
CommandPlacements-Element gruppiert CommandPlacement-Elementen und anderen CommandPlacements Gruppierungen.  
  
 CommandPlacements-Element ist optional. Wenn keine Befehle, Gruppen oder Menüs in einem sekundären Standort berücksichtigt werden müssen, müssen Sie nicht in diesem Abschnitt in der VSCT-Datei enthalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|CommandPlacements|Gruppen CommandPlacement-Elementen und anderen CommandPlacements Gruppierungen.|  
|[CommandPlacement-Element](../extensibility/commandplacement-element.md)|Können Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder ein Menü einbezogen werden.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle darstellen.|  
  
## <a name="example"></a>Beispiel  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CommandPlacement-Element](../extensibility/commandplacement-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)


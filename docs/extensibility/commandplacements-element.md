---
title: CommandPlacements-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21978fef22f704c30de2859725fb2f5e704fcefc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886357"
---
# <a name="commandplacements-element"></a>CommandPlacements-element
CommandPlacements-Element gruppiert CommandPlacement-Elementen und anderen CommandPlacements Gruppierungen.  
  
 CommandPlacements-Element ist optional. Wenn keine Befehle, Gruppen oder Menüs in einem sekundären Standort berücksichtigt werden müssen, müssen Sie nicht in diesem Abschnitt in enthalten Ihre *VSCT* Datei.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
|[CommandPlacement-element](../extensibility/commandplacement-element.md)|Können Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder ein Menü einbezogen werden.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle darstellen.|  
  
## <a name="example"></a>Beispiel  
  
```xml  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CommandPlacement-element](../extensibility/commandplacement-element.md)   
 [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
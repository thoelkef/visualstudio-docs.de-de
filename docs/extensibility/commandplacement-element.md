---
title: CommandPlacement Element | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49de1e1cb41c13ef9b587689f36e302bcadf890c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="commandplacement-element"></a>CommandPlacement-Element
Das Element CommandPlacement kann Schaltflächen, Gruppen und Menüs, die in mehr als eine Gruppe oder einem Menü eingeschlossen werden. Verwenden Sie das CommandPlacement-Element, müssen Sie keinen vollständig diese Elemente neu definieren, um die Darstellung einer Benutzeroberfläche zu ändern.  
  
 Weitere Informationen finden Sie unter [erstellen Wiederverwendbarer Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. Die Guid für den Befehlssatz, gemäß der [Symbole Element](../extensibility/symbols-element.md).|  
|ID|Erforderlich. Die Id des Menüs, Gruppe oder Befehl ein, um die Platzierung gemäß Definition in der `Symbols Element`.|  
|priority|Erforderlich. Bestimmt die visuelle Position des Elements in seinem übergeordneten Element.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Erforderlich. Das Menü oder die Gruppe, die das Element platziert werden hostet.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Gibt Gruppen CommandPlacements und CommandPlacement Elementen.|  
  
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
 [CommandPlacements-Element](../extensibility/commandplacements-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: CommandPlacement-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e52adb46f2a1e4532c5a1c4e00ddddf9e56b96b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289613"
---
# <a name="commandplacement-element"></a>CommandPlacement-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandPlacement-Element kann die Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder ein Menü einbezogen werden. Verwenden Sie das CommandPlacement-Element, müssen Sie keinen dieser Elemente vollständig neu definieren, um das Aussehen einer Benutzeroberfläche zu ändern.  
  
 Weitere Informationen finden Sie unter [Erstellen von Wiederverwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. Die Guid für den Befehlssatz, gemäß der [Symbols-Element](../extensibility/symbols-element.md).|  
|ID|Erforderlich. Die Id der Menüs, eine Gruppe oder ein Befehl aus, um die Platzierung gemäß der `Symbols Element`.|  
|priority|Erforderlich. Bestimmt die visuelle Position des Elements in seinem übergeordneten Element.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Erforderlich. Der im Menü oder die Gruppe, die das Element platziert werden hostet.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Gibt Gruppen von CommandPlacements und CommandPlacement-Elementen.|  
  
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


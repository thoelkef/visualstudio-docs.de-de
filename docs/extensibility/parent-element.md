---
title: Übergeordnetes Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbfb014e57f793bb39d696ac311c4f27884500f4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949716"
---
# <a name="parent-element"></a>Übergeordnetes Element
Das übergeordnete Element eines Felds Schaltfläche oder ein Kombinationsfeld kann nur eine Gruppe sein. Das übergeordnete Element eines Menü oder einer Gruppe kann einem anderen Menü oder einer Gruppe sein. In einem [CommandPlacement-Element](../extensibility/commandplacement-element.md), dieses Element ist erforderlich; in allen anderen Fällen ist er optional. Wenn dieses Element nicht angegeben ist, das übergeordnete Element des `Group_Undefined:0` wird abgeleitet werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID der GUID/ID Befehlsbezeichner.|  
|id|Erforderlich. ID des GUID/ID Befehlsbezeichner.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle, die eine VSPackage bietet die integrierte Entwicklungsumgebung (IDE) darstellen. Beispielsweise Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.|  
|[Buttons-element](../extensibility/buttons-element.md)|Gruppen [Schaltflächenelement](../extensibility/button-element.md) Elemente.|  
|[Menus-element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|  
|[Groups-element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen eines VSPackage definieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
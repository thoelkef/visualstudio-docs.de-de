---
title: Übergeordnetes Element | Microsoft-Dokumentation
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
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62096a713e84353ab79206c5edc7003ab443adbb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765874"
---
# <a name="parent-element"></a>Parent-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das übergeordnete Element eines Felds Schaltfläche oder ein Kombinationsfeld kann nur eine Gruppe sein. Das übergeordnete Element eines Menü oder einer Gruppe kann einem anderen Menü oder einer Gruppe sein. In einem [CommandPlacement-Element](../extensibility/commandplacement-element.md), dieses Element ist erforderlich; in allen anderen Fällen ist er optional. Wenn dieses Element nicht angegeben ist, das übergeordnete Element des `Group_Undefined:0` wird abgeleitet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Keiner  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle, die eine VSPackage bietet die integrierte Entwicklungsumgebung (IDE) darstellen. Beispielsweise Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.|  
|[Buttons-Element](../extensibility/buttons-element.md)|Gruppen [Schaltflächenelement](../extensibility/button-element.md) Elemente.|  
|[Menus-Element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|  
|[Groups-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen eines VSPackage definieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)


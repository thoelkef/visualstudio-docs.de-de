---
title: VisibilityConstraints-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ade6f2ac15d5b1c46b9b388d13b52d87129a66b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930270"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints-element
VisibilityConstraints-Element bestimmt die statische Sichtbarkeit von Gruppen von Befehle und Symbolleisten. Die Sichtbarkeit wird zuerst gesteuert, von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) ohne das VSPackage zu laden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[VisibilityItem-element](../extensibility/visibilityitem-element.md)|Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Bestimmt die statische Sichtbarkeit von Gruppen von Befehle und Symbolleisten.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern) darstellen, die eine VSPackage für der IDE bereitstellt.|  
  
## <a name="example"></a>Beispiel  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VisibilityItem-element](../extensibility/visibilityitem-element.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
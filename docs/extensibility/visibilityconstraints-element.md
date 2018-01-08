---
title: VisibilityConstraints Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 946fc12ab7a77aa72d5d09f7ba9522723f8e18b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints-Element
Das Element VisibilityConstraints bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten. Die Sichtbarkeit wird zunächst vom gesteuert der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) ohne laden das VSPackage.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|[VisibilityItem-Element](../extensibility/visibilityitem-element.md)|Bestimmt die Sichtbarkeit statische, Befehle und Symbolleisten.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern) darstellen, die eine VSPackage mit der IDE ermöglicht.|  
  
## <a name="example"></a>Beispiel  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VisibilityItem-Element](../extensibility/visibilityitem-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
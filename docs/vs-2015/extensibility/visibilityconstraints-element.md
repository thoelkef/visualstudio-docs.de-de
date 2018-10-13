---
title: VisibilityConstraints-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5b290884a2377cdaba573788f0881ec82a19cdf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222377"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VisibilityConstraints-Element bestimmt die statische Sichtbarkeit von Gruppen von Befehle und Symbolleisten. Die Sichtbarkeit wird zuerst gesteuert, von der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) ohne das VSPackage zu laden.  
  
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
|[VisibilityItem-Element](../extensibility/visibilityitem-element.md)|Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Bestimmt die statische Sichtbarkeit von Gruppen von Befehle und Symbolleisten.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle (z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern) darstellen, die eine VSPackage für der IDE bereitstellt.|  
  
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


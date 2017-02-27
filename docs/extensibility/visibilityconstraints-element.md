---
title: "VisibilityConstraints-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, VisibilityConstraints"
  - "VisibilityConstraints-Element (VSCT-XML-Schema)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# VisibilityConstraints-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Element VisibilityConstraints bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten. Die Sichtbarkeit wird zuerst gesteuert, indem die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) ohne das VSPackage geladen.  
  
## Syntax  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[VisibilityItem\-Element](../extensibility/visibilityitem-element.md)|Bestimmt die Sichtbarkeit statische, Befehle und Symbolleisten.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Bestimmt die Sichtbarkeit statische Gruppen von Befehlen und Symbolleisten.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle \(z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder\) darstellen, die einem VSPackage in der IDE bietet.|  
  
## Beispiel  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Siehe auch  
 [VisibilityItem\-Element](../extensibility/visibilityitem-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
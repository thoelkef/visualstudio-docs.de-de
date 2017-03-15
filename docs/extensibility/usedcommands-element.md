---
title: "UsedCommands-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsedCommands"
helpviewer_keywords: 
  - "UsedCommands-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, UsedCommands"
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# UsedCommands-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Element UsedCommands Gruppen UsedCommand Elemente und UsedCommands b.  
  
 Das UsedCommands\-Element ist optional. Wenn Sie nicht außerhalb des Pakets definiert Befehle aufrufen, müssen Sie keinen dieser Abschnitt in der VSCT\-Datei enthalten.  
  
## Syntax  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
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
|[UsedCommand\-Element](../extensibility/usedcommand-element.md)|Der Befehl, der durch anderen Code implementiert wird.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle \(z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder\), die ein VSPackage bietet auf der integrated Development Environment \(IDE\) darstellen.|  
  
## Beispiel  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## Siehe auch  
 [UsedCommand\-Element](../extensibility/usedcommand-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
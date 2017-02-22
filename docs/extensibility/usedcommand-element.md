---
title: "UsedCommand-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UsedCommands-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, UsedCommands"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# UsedCommand-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ermöglicht es einem VSPackage auf einen Befehl, der in einer anderen VSCT\-Datei definiert ist. Angenommen, Ihr VSPackage standardmäßiger **Kopieren** Befehl, der definiert wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell, können Sie den Befehl hinzufügen zu einem Menü oder Symbolleiste ohne erneut zu implementieren.  
  
## Syntax  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die GUID die GUID\-ID\-Paar, die mit dem Befehl bezeichnet.|  
|ID|Erforderlich. Die ID des GUID\-ID\-Paars, die den Befehl bezeichnet.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Keine||  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[UsedCommands\-Element](../extensibility/usedcommands-element.md)|Gruppen UsedCommand Elementen und anderen UsedCommands Gruppierungen.|  
  
## Hinweise  
 Durch Hinzufügen eines Befehls in der `<UsedCommands>` \-Element, ein VSPackage informiert die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung VSPackage mit dem Befehl erforderlich. Hinzufügen einer `<UsedCommand>` \-Element für jeden Befehl, der das Paket erfordert, dass möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten. Angenommen, Ihr Paket einen Befehl aufruft, Visual C\+\+\-spezifisch ist, mit dem Befehl wird nicht für Benutzer von Visual Web Developer, sofern Sie keine `<UsedCommand>` \-Element für den Befehl.  
  
## Beispiel  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## Siehe auch  
 [UsedCommands\-Element](../extensibility/usedcommands-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
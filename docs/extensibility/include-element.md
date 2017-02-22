---
title: "Include-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Include"
helpviewer_keywords: 
  - "Include-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, einschließen"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Include-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Include\-Element gibt eine Datei an, die gefunden werden, kann auf den angegebenen Pfad für das Einfügen in die aktuelle Datei enthalten sein.  Alle Symbole und definierten Typen werden für das kompilierte Ergebnis verwendet.  
  
## Syntax  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|href|Erforderlich. Der Pfad der Headerdatei:<br /><br /> href\="stdidcmd.h"|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Keine.|Keine|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen – d. h. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder –, die ein VSPackage stellt der IDE bereit.|  
  
## Beispiel  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
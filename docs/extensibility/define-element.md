---
title: "Definieren von Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, definieren"
  - "-Element (VSCT-XML-Schema)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Definieren von Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert ein Symbol Name\-Wert\-Paar. Dieses Symbol kann von bedingten Attribute ausgewertet werden. Weitere Informationen finden Sie unter [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md). Siehe auch die [Symbole\-Element](../extensibility/symbols-element.md).  
  
## Syntax  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Name|Erforderlich. Der Name des Symbols:<br /><br /> Name \= "Mode"|  
|Wert|Erforderlich. Der Wert des Symbols:<br /><br /> Wert \= "Standard"|  
|Bedingung|Optional. Weitere Informationen finden Sie unter [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle, die ein VSPackage bietet auf der integrated Development Environment \(IDE\) darstellen. Z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.|  
  
## Beispiel  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
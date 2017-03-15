---
title: "Extern-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Extern"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, Extern"
  - "Extern-Element (VSCT-XML-Schema)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Extern-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das externe Element verweist auf beliebige externe Headerdateien \(. h\), die mit der VSCT\-Datei zur Kompilierungszeit zusammengeführt. Die Dateien, die zusammengeführt werden muss auf dem Include\-Pfad für den Compiler VSCT angegeben oder auf die verwiesen wird ein [Include\-Element](../extensibility/include-element.md). Die Dateien sind möglicherweise andere VSCT\-Dateien oder C\+\+\-Headerdateien.  
  
 Definitionen in Headerdateien muss das Format "\#define \[Symbol\] \[Wert\]" der Wert kann ein anderes Symbol sein, wenn er zuvor definiert ist. Definitionen können in bedingten Anweisungen Befehl Elemente verwendet werden. Jedes Symbol nicht verwendet werden, werden verworfen.  
  
 CommandTable Element  
Extern Element  
  
## Syntax  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|href|Erforderlich. Der Pfad der Headerdatei:<br /><br /> href\="stdidcmd.h"|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Optional. Die Standardsprache für alle [\< Zeichenfolgen \>](../extensibility/strings-element.md) Elemente in der Befehlstabelle:<br /><br /> Language \= "En\-us"|  
  
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
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
---
title: "VSCT XML-Schemareferenz | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Befehl Tabelle Konfigurationsdateien (VSCT), XML-schema"
  - "VSCT XML-Schemaelemente"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# VSCT XML-Schemareferenz
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bietet eine Tabelle mit dem Befehl Tabelle Compiler Schemaelemente, untergeordnete Elemente und Attribute für jeden.  
  
 Eine XML\-basierten Befehl Tabelle\-Konfigurationsdatei \(VSCT\) definiert die Befehlselemente, die ein VSPackage bietet auf der integrated Development Environment \(IDE\). Diese Elemente beinhalten Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.  
  
> [!NOTE]
>  Der VSCT\-Compiler kann einen Präprozessor auf der VSCT\-Datei ausgeführt werden. Da dies i. d. r. der C\+\+\-Präprozessor, Sie definieren können, gehören und Makros verfügen, die die gleiche Syntax, die in C\+\+\-Dateien verwendet wird. Beispiele hierfür stehen in der VSCT\-Datei, die **Neues Projekt** \-Assistent erstellt für ein VSPackage\-Projekt.  
  
## Optionale Elemente  
 Einige VSCT\-Elemente sind optional. Wenn ein `Parent` Argument nicht angegeben ist, wird Group\_Undefined:0 impliziert werden. Wenn ein `Icon` Argument nicht angegeben ist, wird GuidOfficeIcon:msotcidNoIcon impliziert werden. Wenn eine Tastenkombination definiert ist, ist die Emulation in der Regel nicht verwendet wird, optional.  
  
 Bitmap\-Elemente können zum Zeitpunkt der Kompilierung eingebettet werden, durch die Angabe des Speicherorts der Bitmap Balken in der `href` Argument. Die Bitmap Streifen ist bei der Zusammenführung kopiert statt aus den Ressourcen der DLL extrahiert. Wenn ein `href` Argument angegeben wird, die `usedList` Argument ist optional, und alle Steckplätze in der Bitmap Streifen gelten verwendet.  
  
 Alle GUID und ID\-Werte müssen mit symbolischen Namen definiert werden. Diese Namen können in den Headerdateien oder VSCT \< Symbole \> Abschnitte definiert werden. Die symbolischen Namen müssen lokal, sein, durch die Elemente der \< Include \> enthalten oder auf \< Extern \>\-Elementen verwiesen wird. Ein symbolischer Namen aus einer Header\-Datei in einem \< Extern \>\-Element angegeben wird, das einfache Muster folgt importiert \#define SYMBOLWERT. Der Wert kann ein anderes Symbol sein, solange dieses Symbols zuvor definiert wurde. GUID\-Definitionen müssen OLE oder C\+\+\-Format aufweisen. ID\-Werte möglicherweise Dezimalstellen oder hexadezimalen Ziffern, die 0 X vorangestellt werden, wie in den folgenden Zeilen dargestellt:  
  
-   {6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0x62, 0xc8}}  
  
 XML\-Kommentare können verwendet werden, aber Round\-Trip GUI\-Tools \(GUI\) können diese ggf. verwerfen. Der Inhalt der \< Annotation \>\-Elemente sind garantiert, unabhängig vom Format beibehalten werden.  
  
## Schemahierarchie  
 VSCT\-Datei hat die folgenden Hauptelemente.  
  
 [CommandTable\-Element](../extensibility/commandtable-element.md)  
  
 [Extern\-Element](../extensibility/extern-element.md)  
  
 [Include\-Element](../extensibility/include-element.md)  
  
 [Definieren von Element](../extensibility/define-element.md)  
  
 [Commands\-Element](../extensibility/commands-element.md)  
  
 [CommandPlacements\-Element](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints\-Element](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings\-Element](../extensibility/keybindings-element.md)  
  
 [UsedCommands\-Element](../extensibility/usedcommands-element.md)  
  
 [Parent\-Element](../extensibility/parent-element.md)  
  
 [Icon\-Element](../extensibility/icon-element.md)  
  
 [Zeichenfolgen\-Element](../extensibility/strings-element.md)  
  
 [Command\-Flag\-Element](../extensibility/command-flag-element.md)  
  
 [Symbole\-Element](../extensibility/symbols-element.md)  
  
 [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehlsrouting in VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
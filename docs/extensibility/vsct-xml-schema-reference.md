---
title: VSCT-XML-Schemareferenz | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8b8b796f4b5740f90a8755bdf158735387eaa90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143539"
---
# <a name="vsct-xml-schema-reference"></a>VSCT-XML-Schemareferenz
Eine Tabelle mit dem Befehl Tabelle Compiler-Schemaelemente, bereitgestellt Elemente und Attribute für jedes mit zulässigen untergeordneten.  
  
 Eine XML-basierten Befehl Tabelle-Konfigurationsdatei (VSCT) definiert die Befehlselemente, die eine VSPackage bereitstellt, der integrierten Entwicklungsumgebung (IDE). Diese Elemente beinhalten Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.  
  
> [!NOTE]
>  VSCT-Compiler kann einen Präprozessor auf die VSCT-Datei ausgeführt. Da dies in der Regel ist der C++-Präprozessor, Sie definieren können, gehören, und Makros haben, die die gleiche Syntax, die in C++-Dateien verwendet wird. Beispiele hierzu finden Sie in der VSCT-Datei mit den **neues Projekt** erstellt der Assistent für ein VSPackage-Projekt.  
  
## <a name="optional-elements"></a>Optionale Elemente  
 Einige VSCT-Elemente sind optional. Wenn ein `Parent` Argument nicht angegeben ist, wird Group_Undefined:0 impliziert werden. Wenn ein `Icon` Argument nicht angegeben ist, wird GuidOfficeIcon:msotcidNoIcon impliziert werden. Wenn eine Tastenkombination definiert ist, ist die Emulation, die in der Regel nicht verwendet wird, optional.  
  
 Bitmap-Elemente können zum Zeitpunkt der Kompilierung eingebettet werden, durch Angeben des Speicherorts für den Bereichsstreifen mithilfe einer Bitmap in der `href` Argument. Die Menüleiste aus mithilfe einer Bitmap wird während der Zusammenführung kopiert anstatt extrahiert die Ressourcen von der DLL. Wenn ein `href` -Argument bereitgestellt wird, die `usedList` Argument ist optional, und alle bereitstellungsslots auf die Bitmap Streifen gelten verwendet.  
  
 Alle GUID- und ID-Werte müssen mit symbolischen Namen definiert werden. Diese Namen können definiert werden, in den Headerdateien oder im VSCT \<Symbole > Abschnitte. Die symbolischen Namen lokal sein, über enthalten \<Include > Elemente, oder von referenzierten \<"extern" > Elemente. Ein symbolischer Namen von einer Headerdatei, die im angegebenen importiert eine \<"extern" >-Element folgt das einfachen Muster #define SYMBOLWERT. Der Wert kann ein anderes Symbol sein, solange dieses Symbol zuvor definiert wurde. GUID-Definitionen müssen das OLE oder C++-Format aufweisen. ID-Werte möglicherweise Dezimalzahlen oder hexadezimale Ziffern, die 0 X vorangestellt werden, wie in den folgenden Zeilen dargestellt:  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0 x 14, 0x5c, 0 x 93, 0x62, 0xc8}}  
  
 XML-Kommentare verwendet werden können, aber Round-Trip grafische Benutzeroberfläche (GUI) Benutzertools möglicherweise verwerfen. Der Inhalt des \<Annotation >-Elemente sind garantiert, unabhängig vom Format beibehalten werden.  
  
## <a name="schema-hierarchy"></a>Schemahierarchie  
 Eine VSCT-Datei hat die folgenden Hauptelemente.  
  
 [CommandTable-Element](../extensibility/commandtable-element.md)  
  
 [Extern-Element](../extensibility/extern-element.md)  
  
 [Include-Element](../extensibility/include-element.md)  
  
 [Define-Element](../extensibility/define-element.md)  
  
 [Commands-Element](../extensibility/commands-element.md)  
  
 [CommandPlacements-Element](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings-Element](../extensibility/keybindings-element.md)  
  
 [UsedCommands-Element](../extensibility/usedcommands-element.md)  
  
 [Parent-Element](../extensibility/parent-element.md)  
  
 [Icon-Element](../extensibility/icon-element.md)  
  
 [Strings-Element](../extensibility/strings-element.md)  
  
 [CommandFlag-Element](../extensibility/command-flag-element.md)  
  
 [Symbols-Element](../extensibility/symbols-element.md)  
  
 [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehlsrouting in VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
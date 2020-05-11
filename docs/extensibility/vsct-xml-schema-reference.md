---
title: VSCT-XML-Schemareferenz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697904"
---
# <a name="vsct-xml-schema-reference"></a>VSCT-XML-Schemareferenz
Stellt eine Tabelle mit Befehlstabellen-Compilerschemaelementen mit zulässigen untergeordneten Elementen und Attributen für jedes bereit.

 Eine XML-basierte Befehlstabellenkonfigurationsdatei (.vsct) definiert die Befehlselemente, die ein VSPackage für die integrierte Entwicklungsumgebung (IDE) bereitstellt. Zu diesen Elementen gehören Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.

> [!NOTE]
> Der VSCT-Compiler kann einen Präprozessor für die .vsct-Datei ausführen. Da es sich in der Regel um den C++-Präprozessor handelt, können Sie Includes und Makros definieren, die dieselbe Syntax aufweisen wie in C++-Dateien. Beispiele hierfür finden Sie in der .vsct-Datei, die der Assistent für **neues Projekt** für ein VSPackage-Projekt erstellt.

## <a name="optional-elements"></a>Optionale Elemente
 Einige VSCT-Elemente sind optional. Wenn `Parent` kein Argument angegeben ist, Group_Undefined:0 wird impliziert. Wenn `Icon` kein Argument angegeben ist, wird guidOfficeIcon:msotcidNoIcon impliziert. Wenn eine Tastenkombination definiert ist, ist die Emulation, die in der Regel nicht verwendet wird, optional.

 Bitmapelemente können zur Kompilierungszeit eingebettet werden, indem `href` der Speicherort des Bitmapstreifens im Argument angegeben wird. Der Bitmap-Strip wird während des Zusammenführens kopiert und nicht aus den Ressourcen der DLL extrahiert. Wenn `href` ein Argument bereitgestellt `usedList` wird, wird das Argument optional, und alle Slots im Bitmap-Strip werden als verwendet betrachtet.

 Alle GUID- und ID-Werte müssen mithilfe symbolischer Namen definiert werden. Diese Namen können in Headerdateien oder \<in VSCT-Symbolen> Abschnitten definiert werden. Die symbolischen Namen müssen \<lokal sein, über Include \<> Elemente eingeschlossen oder von extern> Elementen referenziert werden. Ein symbolischer Name wird aus einer \<Headerdatei importiert, die in einem extern>-Element angegeben ist, wenn er dem einfachen Muster von #define SYMBOL VALUE folgt. Der Wert kann ein anderes Symbol sein, solange dieses Symbol zuvor definiert wurde. GUID-Definitionen müssen entweder dem OLE- oder C++-Format folgen. ID-Werte können entweder Dezimalstellen oder hexadezimale Ziffern sein, denen 0x vorangestellt ist, wie in den folgenden Zeilen dargestellt:

- 6D484634-E53D-4a2c-ADCB-55145C9362C8

- 0x6d484634, 0xe53d, 0x4a2c, 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8

  XML-Kommentare können verwendet werden, aber ROUND-Trip-Tools für die grafische Benutzeroberfläche (GUI) können sie verwerfen. Der Inhalt \<von Annotation> Elemente werden garantiert unabhängig vom Format beibehalten.

## <a name="schema-hierarchy"></a>Schemahierarchie
 Eine .vsct-Datei enthält die folgenden Hauptelemente.

- [CommandTable-Element](../extensibility/commandtable-element.md)

- [Externes Element](../extensibility/extern-element.md)

- [Include-Element](../extensibility/include-element.md)

- [Definieren des Elements](../extensibility/define-element.md)

- [Befehlselement](../extensibility/commands-element.md)

- [CommandPlacements-Element](../extensibility/commandplacements-element.md)

- [VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)

- [KeyBindings-Element](../extensibility/keybindings-element.md)

- [UsedCommands-Element](../extensibility/usedcommands-element.md)

- [Übergeordnetes Element](../extensibility/parent-element.md)

- [Icon-Element](../extensibility/icon-element.md)

- [Strings-Element](../extensibility/strings-element.md)

- [Befehls-Flag-Element](../extensibility/command-flag-element.md)

- [Symbols-Element](../extensibility/symbols-element.md)

- [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Weitere Informationen
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehlsrouting in VSPackages](../extensibility/internals/command-routing-in-vspackages.md)

---
title: 'How to: Modify a Standard Menu Command in a Domain-Specific Language | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 989367d395abb56e4f57c4aa2694b5f4ef17fb6e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300879"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Gewusst wie: Ändern eines Standardmenübefehls in einer domänenspezifischen Sprache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das Verhalten einiger Standardbefehle ändern, die automatisch im DSL definiert sind. For example, you could modify **Cut** so that it excludes sensitive information. Hierzu überschreiben Sie Methoden in einer festgelegten Klasse des Befehls. Diese Klassen sind in der CommandSet.cs-Datei im DslPackage-Projekt definiert und von <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> abgeleitet.

 Alles in allem ändern Sie einen Befehl folgendermaßen:

1. [Discover what commands you can modify](#what).

2. [Create a partial declaration of the appropriate command set class](#extend).

3. [Override the ProcessOnStatus and ProcessOnMenu methods](#override) for the command.

   In diesem Thema wird diese Vorgehensweise erläutert.

> [!NOTE]
> If you want to create your own menu commands, see [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a> What commands can you modify?

#### <a name="to-discover-what-commands-you-can-modify"></a>So ermitteln Sie, welche Befehle Sie ändern können

1. In the `DslPackage` project, open `GeneratedCode\CommandSet.cs`. This C# file can be found in Solution Explorer as a subsidiary of `CommandSet.tt`.

2. Find classes in this file whose names end with "`CommandSet`", for example `Language1CommandSet` and `Language1ClipboardCommandSet`.

3. Geben Sie in jeder festgelegten Klasse des Befehls "`override`" gefolgt von einem Leerzeichen ein. IntelliSense zeigt eine Liste der Methoden an, die Sie überschreiben können. Jeder Befehl verfügt über ein Paar von Methoden, deren Namen mit "`ProcessOnStatus`" und "`ProcessOnMenu`" beginnen.

4. Beachten Sie, welche der festgelegten Klassen des Befehls den Befehl enthält, den Sie verändern möchten.

5. Schließen Sie die Datei, ohne Ihre Änderungen zu speichern.

    > [!NOTE]
    > Normalerweise sollten Sie keine Dateien bearbeiten, die generiert wurden. Änderungen gehen verloren, wenn die Dateien das nächste Mal generiert werden.

## <a name="extend"></a> Extend the appropriate command set class
 Erstellen Sie eine neue Datei, die eine partielle Deklaration der festgelegten Klasse des Befehls enthält.

#### <a name="to-extend-the-command-set-class"></a>So erweitern Sie die festgelegte Klasse des Befehls

1. Öffnen Sie im Projektmappen-Explorer im Projekt "DslPackage" den Ordner "GeneratedCode". Suchen Sie unter "CommandSet.tt" die generierte Datei "CommandSet.cs", und öffnen Sie sie. Notieren Sie sich den Namespace und den Namen der ersten dort definierten Klasse. Es wird beispielsweise Folgendes angezeigt:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. In **DslPackage**, create a folder named **Custom Code**. In this folder, create a new class file named `CommandSet.cs`.

3. Schreiben Sie in die neue Datei eine partielle Deklaration mit demselben Namespace und Namen wie die generierte partielle Klasse. Beispiel:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Note** If you used the class file template to create the new file, you must correct both the namespace and the class name.

## <a name="override"></a> Override the command methods
 Most commands have two associated methods: The method with a name like `ProcessOnStatus`... determines whether the command should be visible and enabled. Sie wird aufgerufen, wenn der Benutzer mit der rechten Maustaste auf das Diagramm klickt und sollte schnell ausgeführt werden sowie keine Änderungen vornehmen. `ProcessOnMenu`... is called when the user clicks the command, and should perform the function of the command. Sie können eine dieser oder beide Methoden überschreiben.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Ändern, wann der Befehl in einem Menü angezeigt wird
 Override the ProcessOnStatus... method. Diese Methode sollte für den Parameter MenuCommand die Eigenschaften "Visible" (sichtbar) und "Enabled" (aktiviert) festlegen. Meist prüft der Befehl CurrentSelection, um zu bestimmen, ob der Befehl auf die ausgewählten Elemente zutrifft. Möglicherweise werden auch die Eigenschaften geprüft, um zu bestimmen, ob der Befehl bei deren aktuellem Status angewendet werden kann.

 Allgemein gilt, die Eigenschaft "Visible" sollte dadurch bestimmt werden, welche Elemente ausgewählt sind. Die Eigenschaft "Enabled", die bestimmt, ob der Befehl im Menü schwarz oder ausgegraut angezeigt wird, sollte vom aktuellen Status der Auswahl abhängen.

 Im folgenden Beispiel wird das Menüelement "Delete" (Löschen) deaktiviert, wenn der Benutzer mehr als eine Form ausgewählt hat.

> [!NOTE]
> Diese Methode beeinflusst nicht, ob der Befehl über eine Tastatureingabe verfügbar ist. Zum Beispiel verhindert das Deaktivieren des Menüelements "Delete" (Löschen) nicht, dass der Befehl über die Entf-Taste ausgelöst wird.

```
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

 Es ist empfehlenswert, zuerst die Basismethode aufzurufen, um alle Fälle und Einstellungen zu behandeln, die nicht enthalten sind.

 Die ProcessOnStatus-Methode sollte Elemente im Speicher nicht erstellen, löschen oder aktualisieren.

### <a name="to-change-the-behavior-of-the-command"></a>So ändern Sie das Verhalten des Befehls
 Override the ProcessOnMenu... method. Im folgenden Beispiel wird der Benutzer davon abgehalten, mehr als ein Element auf einmal zu löschen, selbst mit der Entf-Taste.

```
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

 Wenn der Code Änderungen am Speicher vornimmt, wie Erstellen, Löschen oder Aktualisieren von Elementen oder Links, muss dies innerhalb einer Transaktion erfolgen. For more information, see [How to Create and Update model elements](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="writing-the-code-of-the-methods"></a>Schreiben des Methodencodes
 Die folgenden Fragmente sind innerhalb dieser Methoden oft hilfreich:

- `this.CurrentSelection` Die Form, die der Benutzer mit der rechten Maustaste angeklickt hat, ist immer in dieser Liste mit Formen und Konnektoren enthalten. Wenn der Benutzer auf einen leeren Bereich des Diagramms klickt, ist das Diagramm das einzige Mitglied der Liste.

- `this.IsDiagramSelected()` - `true` if the user clicked a blank part of the diagram.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - the user did not select multiple shapes

- `this.SingleSelection` – die Form oder das Diagramm, auf das der Benutzer mit der rechten Maustaste geklickt hat

- `shape.ModelElement as MyLanguageElement` – das Modellelement, das durch eine Form dargestellt wird

  For more information about how to navigate from element to element and about how to create objects and links, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Siehe auch
 <xref:System.ComponentModel.Design.MenuCommand> [Writing Code to Customise a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md) [How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) [Walkthrough: Getting Information from a Selected Link](../misc/walkthrough-getting-information-from-a-selected-link.md) [How VSPackages Add User Interface Elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML Schema Reference](../extensibility/vsct-xml-schema-reference.md)

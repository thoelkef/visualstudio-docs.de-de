---
title: 'Gewusst wie: Ändern eines Standard Menübefehls in einer domänenspezifischen Sprache | Microsoft-Dokumentation'
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

Sie können das Verhalten einiger Standardbefehle ändern, die automatisch im DSL definiert sind. Beispielsweise können Sie " **Ausschneiden** " so ändern, dass sensible Informationen ausgeschlossen werden. Hierzu überschreiben Sie Methoden in einer festgelegten Klasse des Befehls. Diese Klassen sind in der CommandSet.cs-Datei im DslPackage-Projekt definiert und von <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> abgeleitet.

 Alles in allem ändern Sie einen Befehl folgendermaßen:

1. [Ermitteln Sie, welche Befehle Sie ändern können](#what).

2. [Erstellen Sie eine partielle Deklaration der entsprechenden Befehlssatz Klasse](#extend).

3. Über [schreiben Sie die processonstatus-Methode und die processonmenu-Methode](#override) für den Befehl.

   In diesem Thema wird diese Vorgehensweise erläutert.

> [!NOTE]
> Wenn Sie eigene Menübefehle erstellen möchten, finden Sie weitere Informationen unter Gewusst [wie: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a>Welche Befehle können Sie ändern?

#### <a name="to-discover-what-commands-you-can-modify"></a>So ermitteln Sie, welche Befehle Sie ändern können

1. Öffnen Sie im Projekt `DslPackage` `GeneratedCode\CommandSet.cs`. Diese C# Datei befindet sich in Projektmappen-Explorer als Tochterunternehmen von `CommandSet.tt`.

2. Suchen Sie in dieser Datei nach Klassen, deren Namen mit "`CommandSet`" enden, z. b. `Language1CommandSet` und `Language1ClipboardCommandSet`.

3. Geben Sie in jeder festgelegten Klasse des Befehls "`override`" gefolgt von einem Leerzeichen ein. IntelliSense zeigt eine Liste der Methoden an, die Sie überschreiben können. Jeder Befehl verfügt über ein Paar von Methoden, deren Namen mit "`ProcessOnStatus`" und "`ProcessOnMenu`" beginnen.

4. Beachten Sie, welche der festgelegten Klassen des Befehls den Befehl enthält, den Sie verändern möchten.

5. Schließen Sie die Datei, ohne Ihre Änderungen zu speichern.

    > [!NOTE]
    > Normalerweise sollten Sie keine Dateien bearbeiten, die generiert wurden. Änderungen gehen verloren, wenn die Dateien das nächste Mal generiert werden.

## <a name="extend"></a>Erweitern der entsprechenden Befehlssatz Klasse
 Erstellen Sie eine neue Datei, die eine partielle Deklaration der festgelegten Klasse des Befehls enthält.

#### <a name="to-extend-the-command-set-class"></a>So erweitern Sie die festgelegte Klasse des Befehls

1. Öffnen Sie im Projektmappen-Explorer im Projekt "DslPackage" den Ordner "GeneratedCode". Suchen Sie unter "CommandSet.tt" die generierte Datei "CommandSet.cs", und öffnen Sie sie. Notieren Sie sich den Namespace und den Namen der ersten dort definierten Klasse. Es wird beispielsweise Folgendes angezeigt:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. Erstellen Sie in **dslpackage**einen Ordner mit dem Namen **benutzerdefinierter Code**. Erstellen Sie in diesem Ordner eine neue Klassendatei mit dem Namen `CommandSet.cs`.

3. Schreiben Sie in die neue Datei eine partielle Deklaration mit demselben Namespace und Namen wie die generierte partielle Klasse. Beispiel:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Hinweis** Wenn Sie die Klassendatei Vorlage verwendet haben, um die neue Datei zu erstellen, müssen Sie sowohl den Namespace als auch den Klassennamen korrigieren.

## <a name="override"></a>Überschreiben der Befehls Methoden
 Die meisten Befehle verfügen über zwei zugeordnete Methoden: die Methode mit einem Namen wie `ProcessOnStatus`... bestimmt, ob der Befehl sichtbar und aktiviert sein soll. Sie wird aufgerufen, wenn der Benutzer mit der rechten Maustaste auf das Diagramm klickt und sollte schnell ausgeführt werden sowie keine Änderungen vornehmen. `ProcessOnMenu`... wird aufgerufen, wenn der Benutzer auf den Befehl klickt, und sollte die Funktion des Befehls ausführen. Sie können eine dieser oder beide Methoden überschreiben.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Ändern, wann der Befehl in einem Menü angezeigt wird
 Überschreiben Sie den processonstatus... anzuwenden. Diese Methode sollte für den Parameter MenuCommand die Eigenschaften "Visible" (sichtbar) und "Enabled" (aktiviert) festlegen. Meist prüft der Befehl CurrentSelection, um zu bestimmen, ob der Befehl auf die ausgewählten Elemente zutrifft. Möglicherweise werden auch die Eigenschaften geprüft, um zu bestimmen, ob der Befehl bei deren aktuellem Status angewendet werden kann.

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
 Überschreiben Sie das processonmenu... anzuwenden. Im folgenden Beispiel wird der Benutzer davon abgehalten, mehr als ein Element auf einmal zu löschen, selbst mit der Entf-Taste.

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

 Wenn der Code Änderungen am Speicher vornimmt, wie Erstellen, Löschen oder Aktualisieren von Elementen oder Links, muss dies innerhalb einer Transaktion erfolgen. Weitere Informationen finden Sie unter [Erstellen und Aktualisieren von Modellelementen](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="writing-the-code-of-the-methods"></a>Schreiben des Methodencodes
 Die folgenden Fragmente sind innerhalb dieser Methoden oft hilfreich:

- `this.CurrentSelection`. Die Form, die der Benutzer mit der rechten Maustaste angeklickt hat, ist immer in dieser Liste mit Formen und Konnektoren enthalten. Wenn der Benutzer auf einen leeren Bereich des Diagramms klickt, ist das Diagramm das einzige Mitglied der Liste.

- `this.IsDiagramSelected()` - `true`, wenn der Benutzer auf einen leeren Teil des Diagramms geklickt hat.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`: der Benutzer hat nicht mehrere Formen ausgewählt.

- `this.SingleSelection`-die Form oder das Diagramm, auf die der Benutzer mit der rechten Maustaste geklickt hat

- `shape.ModelElement as MyLanguageElement`-das Modellelement, das durch eine Form dargestellt wird.

  Weitere Informationen zum Navigieren von einem Element zu einem Element und zum Erstellen von Objekten und Links finden Sie unter [navigieren und Aktualisieren eines Modells im Programm Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Siehe auch
 <xref:System.ComponentModel.Design.MenuCommand> [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md) Gewusst [wie: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) Exemplarische Vorgehensweise [: erhalten von Informationen von einem ausgewählten Link](../misc/walkthrough-getting-information-from-a-selected-link.md) Gewusst [wie: Hinzufügen von Benutzeroberflächen Elementen](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [Visual Studio Command Table (. Vsct-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) ( [vsct-XML-Schema Referenz](../extensibility/vsct-xml-schema-reference.md) )

---
title: Erweitern von Visual Studio für Mac
description: Die Funktionen von Visual Studio für Mac können mit Modulen erweitert werden, die Erweiterungspakete genannt werden. Der erste Teil dieser Anleitung erstellt ein einfaches Erweiterungspaket für Visual Studio für Mac, um das Datum und die Uhrzeit in ein Dokument einzufügen. Der zweite Teil dieser Anleitung erläutert die Grundlagen des Erweiterungspaketsystems und einige der wichtigsten APIs, die die Grundlage von Visual Studio für Mac bilden.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 29c5bb9c45ae8d859316bd9c63eec10a6a425571
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851954"
---
# <a name="extending-visual-studio-for-mac"></a>Erweitern von Visual Studio für Mac

Visual Studio für Mac besteht aus einem Satz von Modulen, die *Erweiterungspakete* genannt werden. Sie können Erweiterungspakete verwenden, um neue Funktionen in Visual Studio für Mac zu integrieren, z.B. die Unterstützung für eine zusätzliche Sprache oder eine neue Projektvorlage.

Erweiterungspakete werden aus den *Erweiterungspunkten* anderer Erweiterungspakete erstellt. Erweiterungspunkte sind Platzhalter für Bereiche, die erweitert werden können, z.B. ein Menü oder die Liste der IDE-Befehle. Ein Erweiterungspaket kann aus einem Erweiterungspunkt erstellt werden, indem ein Knoten strukturierter Daten, auch Erweiterung genannt, z.B. ein neues Menüelement oder ein neuer Befehl, registriert wird. Jeder Erweiterungspunkt akzeptiert bestimmte Erweiterungstypen, z.B. einen *Befehl*, ein *Pad* oder eine *Dateivorlage*. Ein Modul, das Erweiterungspunkte enthält, wird *Add-In-Host* genannt, da es durch andere Erweiterungspakete erweitert werden kann.

Um Visual Studio für Mac anzupassen, können Sie ein Erweiterungspaket erstellen, das aus Erweiterungspunkten erstellt wird, die in Add-In-Hosts innerhalb vorhandener Bibliotheken in Visual Studio für Mac enthalten sind, wie durch das folgende Diagramm dargestellt:

![Add-In-Architektur](media/extending-visual-studio-mac-addin1.png)

Damit ein Erweiterungspaket aus Visual Studio für Mac erstellen kann, muss es über Erweiterungen verfügen, die aus bereits vorhandenen Erweiterungspunkten innerhalb der Visual Studio für Mac-IDE erstellen. Wenn sich ein Erweiterungspaket auf einen Erweiterungspunkt verlässt, der in einem Add-In-Host definiert ist, wird diesem eine  _Abhängigkeit_  von diesem Erweiterungspaket nachgesagt.

Der Vorteil dieses modularen Aufbaus ist, dass Visual Studio für Mac erweiterbar ist. Es existieren viele Erweiterungspunkte, die mit benutzerdefinierten Erweiterungspaketen erweitert werden können. Beispiele für aktuelle Erweiterungspakete umfassen die Unterstützung für C# und F#, Debuggertools und Projektvorlagen.

> [!NOTE]
> Wenn Sie über ein Add-in-Maker-Projekt verfügen, das vor Add-in-Maker 1.2 erstellt wurde, müssen Sie Ihr Projekt wie in den [hier](https://mhut.ch/addinmaker/1.2) beschriebenen Schritten migrieren.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Dieser Abschnitt befasst sich mit den verschiedenen Dateien, die vom Add-in Maker generiert werden, sowie mit den Daten, die von einer Befehlserweiterung benötigt werden.

## <a name="attribute-files"></a>Attributdateien

Erweiterungspakete speichern Metadaten über ihren Namen, ihre Version, Abhängigkeiten und andere Informationen in C#-Attributen. Der Add-in Maker erstellt zwei Dateien, `AddinInfo.cs` und `AssemblyInfo.cs`, um diese Informationen zu speichern und zu organisieren. Erweiterungspakete müssen über eine eindeutige ID und einen eindeutigen Namespace verfügen, der in deren *-Add-in-Attribut* angegeben wird:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Erweiterungspakete müssen auch Abhängigkeiten von den Erweiterungspaketen deklarieren, die die Erweiterungspunkte besitzen, in die sie eingebunden werden. Auf diese wird zum Zeitpunkt der Erstellung automatisch verwiesen.

Darüber hinaus können zusätzliche Verweise über den Add-in-Verweisknoten im Projektmappenpad für das Projekt hinzugefügt werden, wie in der folgenden Abbildung dargestellt:

![Screenshot vom Einfügen des Datums](media/extending-visual-studio-mac-addin13.png)

Zudem werden die entsprechenden `assembly:AddinDependency`-Attribute zum Zeitpunkt der Erstellung hinzugefügt. Sobald die Metadaten und Abhängigkeitsdeklarationen vorhanden sind, können Sie den Fokus auf die wichtigen Bausteine des Erweiterungspakets legen.

## <a name="extensions-and-extension-points"></a>Erweiterungen und Erweiterungspunkte

Ein Erweiterungspunkt ist ein Platzhalter, der eine Datenstruktur (einen Typ) definiert, während eine Erweiterung Daten definiert, die einer Struktur entsprechen, die durch einen bestimmten Erweiterungspunkt festgelegt wird. Erweiterungspunkte geben an, welchen Typ von Erweiterung sie in ihrer Deklaration akzeptieren können. Erweiterungen werden mithilfe von Namen oder Erweiterungspfaden deklariert. Eine tiefer greifende Erklärung dazu, wie Sie den Erweiterungspunkt erstellen, den Sie benötigen, finden Sie in der [Referenz zu Erweiterungspunkten](https://github.com/mono/mono-addins/wiki/Extension-Points).

Durch die Erweiterung/Erweiterungspunkt-Architektur bleibt die Entwicklung von Visual Studio für Mac schnell und modular.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Befehlserweiterungen

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Befehlserweiterungen sind Erweiterungen, die auf Methoden verweisen, die jedes Mal aufgerufen werden, wenn sie ausgeführt werden.

Befehlserweiterungen werden durch das Hinzufügen von Einträgen zum Erweiterungspunkt `/MonoDevelop/Ide/Commands` definiert. Wir haben unsere Erweiterung in `Manifest.addin.xml` mit dem folgenden Code definiert:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Der Erweiterungsknoten enthält ein path-Attribut, das den Erweiterungspunkt angibt, in den er eingebettet ist, in diesem Fall `/MonoDevelop/Ide/Commands/Edit`. Darüber hinaus fungiert er als übergeordneter Knoten für den Befehl. Der Befehlsknoten verfügt über die folgenden Attribute:

* **id**: Gibt den Bezeichner für diesen Befehl an. Befehlsbezeichner müssen als Enumerationsmember deklariert werden und werden dazu verwendet, Befehle mit Befehlselementen zu verbinden.
* **_label**: Der Text, der in Menüs angezeigt werden soll.
* **_description**: Der Text, der als QuickInfo für Symbolleistenschaltflächen angezeigt werden soll.
* **defaultHandler**: Gibt die `CommandHandler`-Klasse an, die den Befehl steuert.

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Der folgende Codeausschnitt zeigt eine CommandItem-Erweiterung, die in den `/MonoDevelop/Ide/MainMenu/Edit`-Erweiterungspunkt eingebunden ist:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

Ein Befehlselement platziert einen in seinem ID-Attribut angegebenen Befehl in einem Menü. Dieses Befehlselement erweitert den Erweiterungspunkt `/MonoDevelop/Ide/MainMenu/Edit`, wodurch die Bezeichnung des Befehls im **Menü „Bearbeiten“** erscheint. Beachten Sie, dass die **ID** im Befehlselement mit der ID des Befehlsknoten, `InsertDate`, übereinstimmt. Wenn Sie das Befehlselement entfernen müssten, würde die Option **Datum einfügen** nicht mehr im Menü „Bearbeiten“ angezeigt.

### <a name="command-handlers"></a>Befehlshandler

`InsertDateHandler` ist eine Erweiterung der `CommandHandler`-Klasse. Es überschreibt zwei Methoden, `Update` und `Run`. Die `Update`-Methode wird immer dann abgerufen, wenn ein Befehl in einem Menü angezeigt oder über Tastenzuordnungen ausgeführt wird. Durch Ändern des Infoobjekts können Sie den Befehl deaktivieren oder unsichtbar machen, Arraybefehle auffüllen u.v.m. Diese `Update`-Methode deaktiviert den Befehl, wenn sie kein aktives *Dokument* mit einem *Texteditor* zum Einfügen von Text findet:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Sie müssen die `Update`-Methode nur überschreiben, wenn Sie über eine besondere Logik zum Aktivieren oder Ausblenden des Befehls verfügen. Die `Run`-Methode wird immer dann ausgeführt, wenn ein Benutzer einen Befehl ausführt, was in diesem Fall auftritt, wenn ein Benutzer den Befehl aus dem Menü „Bearbeiten“ auswählt. Diese Methode fügt das Datum und die Uhrzeit an der Einfügemarke im Texteditor ein:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Deklarieren Sie den Befehlstyp als Enumerationsmember innerhalb von `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Dadurch werden der Befehl und das Befehlselement verknüpft: Das Befehlselement ruft den Befehl auf, wenn das Befehlselement aus dem **Menü „Bearbeiten“** ausgewählt wird.

## <a name="ide-apis"></a>IDE-APIs

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Informationen zum Umfang der Bereiche, die für die Entwicklung verfügbar sind, finden Sie unter [Extension Tree Reference (Referenz zur Erweiterungsstruktur)](https://www.monodevelop.com/developers/articles/extension-tree-reference/) und [API Overview (API-Übersicht)](https://www.monodevelop.com/developers/articles/api-overview/). Beim Erstellen von ausgeweiteten Erweiterungspaketen lesen Sie sich auch [Entwicklerartikel](https://www.monodevelop.com/developers/articles/) durch. Nachfolgend finden Sie eine partielle Liste von Bereichen für die Anpassung:

* Pads
* Tastenzuordnungsschemas
* Richtlinien
* Codeformatierungsprogramme
* Projektdateiformate
* Panel „Einstellungen“
* Panel „Optionen“
* Debuggerprotokolle
* Debuggerschnellansichten
* Arbeitsbereichlayouts
* Projektmappenpad-Strukturknoten
* Seitenränder des Quellcode-Editors
* Unittest-Engines
* Codegeneratoren
* Codeausschnitte
* Zielframeworks
* Ziellaufzeit
* VCS-Back-Ends
* Umgestaltung
* Ausführungshandler
* Syntaxhervorhebung

## <a name="additional-information"></a>Zusätzliche Informationen

> [!NOTE]
> Wir arbeiten derzeit an der Verbesserung der Erweiterbarkeitsszenarios für Visual Studio für Mac. Wenn Sie Erweiterungen erstellen und zusätzliche Hilfe oder Informationen benötigen bzw. Feedback geben möchten, füllen Sie bitte das [Visual Studio for Mac Extension Authoring](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u)-Formular (Erstellung von Erweiterungen für Visual Studio für Mac) aus.

## <a name="see-also"></a>Siehe auch

- [Entwickeln von Visual Studio-Erweiterungen (unter Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)

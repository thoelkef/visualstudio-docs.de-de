---
title: Verwalten von Projekt- und Projektmappeneigenschaften
description: In diesem Artikel erfahren Sie, wie Sie die Eigenschaften von Projekten und Projektmappen in Visual Studio für Mac verwalten können.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 514792804515541b7e4f64359a08e9c6093c5018
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692883"
---
# <a name="managing-project-and-solution-properties"></a>Verwalten von Projekt- und Projektmappeneigenschaften

## <a name="project-options"></a>Projektoptionen

Die Projektoptionen sind für jedes Projekt spezifisch und beeinflussen, wie das Projekt geschrieben, erstellt und ausgeführt wird. Dies steht im Gegensatz zu den Einstellungen für Visual Studio für Mac (die benutzerdefinierte Optionen festlegen) und zu den Projektmappenoptionen (die Optionen für die gesamte Projektmappe festlegen). Projektoptionen werden in der Projektdatei (.csproj) gespeichert, sodass andere Entwickler das Projekt ordnungsgemäß erstellen und ausführen können. Mit spezifischen Projektoptionen können viele Entwickler am gleichen Dokument arbeiten, ohne die Formatierung der Datei zu beeinträchtigen.

Doppelklicken Sie zum Öffnen von Projektoptionen in Visual Studio für Mac auf den Projektnamen, oder machen Sie einen Doppelklick darauf, um das Kontextmenü zu öffnen. Wählen Sie anschließend **Optionen** aus:

![Optionen im Kontextmenü](media/projects-and-solutions-image2.png)

Zu den bearbeitbaren Optionen gehören Optionen zum Erstellen, Ausführen und Festlegen von Quellcode und Optionen zur Versionskontrolle.

Projektoptionen sind in fünf verschiedene Kategorien unterteilt:

* **Allgemein**: Projektinformationen wie zum Beispiel Name, Beschreibung und Standardnamespace werden hier festgelegt, ebenso wie der Speicherort des Projekts.
* **Erstellen**: Dadurch wird es Entwicklern ermöglicht, PCL-Profile für portable Klassenbibliotheken festzulegen oder zu ändern. Es können auch benutzerdefinierte Befehle, Konfigurationen und Compileroptionen festgelegt werden. Der Ausgabepfad und der Assemblyname können hier ebenfalls festgelegt werden.
* **Ausführen**: Dadurch können Sie benutzerdefinierte Konfigurationen pro Projekt erstellen.
* **Quellcode**: Dadurch können Sie die Formatierung von vielen verschiedenen Dateitypen und Namenskonventionen steuern. Hier können Sie auch Benennungsrichtlinien und Standard-Headerstile festlegen.
* **Versionskontrolle**: Dadurch können Sie den Stil der Commit-Nachricht bearbeiten, wenn Sie Versionskontrolle für Ihr Projekt verwenden.

Jedes Projekt kann abhängig von der Plattform bestimmte Projektoptionen enthalten. Beispielsweise verfügt ein Xamarin.Android-Projekt wie das in der folgenden Abbildung dargestellte über Optionen, die sich auf den Android Build beziehen (z.B. Linkeroptionen) und auf die Anwendung (z.B. Berechtigungen):

![Optionen für Android-Projekte](media/projects-and-solutions-image5.png)

Xamarin.iOS enthält Optionen, die sich auf die Bundlesignierung beziehen, zum Beispiel das zur Verwendung erforderliche Bereitstellungsprofil:

![iOS-Projektoptionen](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Projektmappenoptionen

Projektmappenoptionen sind wie Projektoptionen, sie decken jedoch den Bereich ganzer Projektmappen ab. Sie stellen Möglichkeiten zum Festlegen von Autorinformationen, Erstellen von Einstellungen sowie Formatierungsstile für Code und Versionskontrolle bereit. Außerdem ermöglichen Sie das Zuweisen des Startprojekts zur Projektmappe.  Auf das Dialogfeld für Projektmappenoptionen kann über das Menüelement **Project > Solution Options** (Projekt > Projektmappenoptionen) , über das Kontextmenüelement **Optionen** im Projektmappenpad der Projektmappe oder durch Doppelklicken auf die Projektmappe im Projektmappenpad zugegriffen werden:

![Projektmappenoptionen](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>Siehe auch

* [Verwalten von Projekt- und Projektmappeneigenschaften (Visual Studio unter Windows)](/visualstudio/ide/managing-project-and-solution-properties)
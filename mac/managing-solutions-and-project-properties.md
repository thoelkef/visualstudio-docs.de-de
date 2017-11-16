---
title: Verwalten von Projekt- und Projektmappeneigenschaften | Microsoft-Dokumentation
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>Verwalten von Projekt- und Projektmappeneigenschaften

## <a name="project-options"></a>Projektoptionen

Die Projektoptionen sind für jedes Projekt spezifisch und beeinflussen, wie das Projekt geschrieben, erstellt und ausgeführt wird. Dies steht im Gegensatz zu den Einstellungen für Visual Studio für Mac, die benutzerdefinierte Optionen festlegen und zu den Projektmappenoptionen, die Optionen für die gesamte Projektmappe festlegen. Projektoptionen werden in der Projektdatei (.csproj) gespeichert, sodass andere Entwickler das Projekt ordnungsgemäß erstellen und ausführen können. Dadurch können viele Entwickler am gleichen Dokument arbeiten, ohne die Formatierung der Datei zu beeinträchtigen.

Die Projektoptionen in Visual Studio für Mac können geöffnet werden, indem Sie doppelt auf den Projektnamen klicken, oder indem Sie mit der rechten Maustaste klicken, um das Kontextmenü zu öffnen und dort auf **Optionen** klicken:

 ![Optionen im Kontextmenü](media/projects-and-solutions-image2.png)

Zu den bearbeitbaren Optionen gehören solche zum Erstellen, Ausführen und Festlegen von Quellcode und Optionen zur Versionskontrolle.

Projektoptionen sind in fünf verschiedene Kategorien unterteilt, die über die folgenden Funktionen verfügen:

* **Allgemein**: Projektinformationen wie zum Beispiel Name, Beschreibung und Standardnamespace können hier festgelegt werden, ebenso wie der Speicherort des Projekts.
* **Erstellen**: Dadurch wird es Entwicklern ermöglicht, PCL-Profile für portable Klassenbibliotheken festzulegen oder zu ändern. Es können auch benutzerdefinierte Befehle, Konfigurationen und Compileroptionen festgelegt werden. Der Ausgabepfad und der Assemblyname können hier ebenfalls festgelegt werden.
* **Ausführen**: Dadurch können Sie benutzerdefinierte Konfigurationen pro Projekt erstellen.
* **Quellcode**: Dadurch können Sie die Formatierung von vielen verschiedenen Dateitypen und Namenskonventionen steuern. Hier können Sie auch Benennungsrichtlinien und Standard-Headerstile festlegen.
* **Versionskontrolle**: Dadurch können Sie den Stil der Commit-Nachricht bearbeiten, wenn Sie Versionskontrolle für Ihr Projekt verwenden.

Jedes Projekt kann abhängig von der Plattform auch bestimmte Projektoptionen enthalten. Beispielsweise verfügt ein Xamarin.Android-Projekt wie das unten dargestellte über Optionen, die sich auf den Android Build beziehen, zum Beispiel Linkeroptionen und auf die Anwendung, zum Beispiel Berechtigungen:

 ![Optionen für Android-Projekte](media/projects-and-solutions-image5.png)

Xamarin.iOS enthält Optionen, die sich auf die Bundlesignierung beziehen, zum Beispiel das zur Verwendung erforderliche Bereitstellungsprofil und welche, die sich auf die Optionen für die IPA-Paketerstellung beziehen:

 ![iOS-Projektoptionen](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Projektmappenoptionen 

Projektmappenoptionen sind wie Projektoptionen, sie decken jedoch den Bereich ganzer Projektmappen ab. Sie stellen Möglichkeiten zum Festlegen von Autorinformationen, Erstellen von Einstellungen sowie Formatierungsstile für Code und Versionskontrolle bereit. Außerdem ermöglichen Sie das Zuweisen des Startprojekts zur Projektmappe.  Auf das Dialogfeld für Projektmappenoptionen kann über das Menüelement **Project > Solution Options** (Projekt > Projektmappenoptionen) , über das Kontextmenüelement **Optionen** im Projektmappenpad der Projektmappe oder durch Doppelklicken auf die Projektmappe im Projektmappenpad zugegriffen werden:

 ![Projektmappenoptionen](media/projects-and-solutions-image7.png)

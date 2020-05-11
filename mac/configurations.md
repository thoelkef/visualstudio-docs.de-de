---
title: Grundlagen der Buildkonfiguration
description: In diesem Artikel erfahren Sie mehr über die verschiedenen Buildkonfigurationen in Visual Studio für Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128400"
---
# <a name="understanding-build-configurations"></a>Grundlagen der Buildkonfiguration

Sie können verschiedene Konfigurationen der Projektmappen- und Projekteigenschaften speichern, die während des Entwicklungsprozesses in unterschiedlichen Arten von Builds verwendet werden können. Projekte, die mithilfe einer Vorlage in Visual Studio für Mac erstellt werden, enthalten in der Regel Debug-und Releasekonfigurationen, die das Debuggen einer App beziehungsweise die Bereitstellung einer App unterstützen. 

Wenn Sie benutzerdefinierte Konfigurationen erstellen möchten, finden Sie weitere Informationen unter [Erstellen und Bearbeiten von Buildkonfigurationen](/visualstudio/mac/create-and-edit-configurations).

>[!NOTE]
>Dieses Thema gilt für Visual Studio für Mac. Informationen zu Visual Studio unter Windows finden Sie unter [Grundlagen der Buildkonfiguration](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Projektmappenkonfigurationen

Projektmappenkonfigurationen werden verwendet, um Konfigurationen für alle Projekte in einer Projektmappe anzugeben. Über die Registerkarte **Konfigurationszuordnungen** unter **Build > Konfigurationen** können Sie eine Zielkonfiguration für jedes Element in der aktuell geöffneten Projektmappe zuweisen. Dies wird in der folgenden Abbildung veranschaulicht:

![Optionen Konfigurationszuordnung](media/projects-and-solutions-image3.png)

Weitere Informationen über Konfigurationen finden Sie in dem Video zum [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) von James Montemagno.

## <a name="project-build-configurations"></a>Projektbuildkonfigurationen

Projekte verfügen tendenziell über mehrere Konfigurationen. Die Konfiguration und Plattform, auf die ein Projekt ausgerichtet ist, werden zusammen verwendet, um die bei der Erstellung zu verwendenden Eigenschaften festzulegen. Wenn Sie zwischen Konfigurationen wechseln, erhalten Sie zur Buildzeit unterschiedliche Ausgaben. Eine Debugkonfiguration gibt z.B. Debuggingsymbole aus, mit denen der Debugger Funktionsnamen, Parameter oder Variablen aus der Stapelüberwachung einer abgestürzten Anwendung auflösen kann. Diese zusätzlichen Informationen sind zwar während der Entwicklung nützlich, blähen die Datei jedoch auf und sind für die Verteilung nicht ideal.

Jede Plattform hat spezifische Konfigurationen für ihre Builds. Sie können auf die Buildkonfigurationsseiten für Projekte zugreifen, indem Sie im Dialogfeld **Projektoptionen** zum Abschnitt **Build** navigieren. Öffnen Sie dieses Dialogfeld, indem Sie mit der rechten Maustaste auf das Projekt klicken und **Optionen** auswählen, oder indem Sie auf das Projekt im Projektmappen-Explorer doppelklicken.

## <a name="run-configuration"></a>Laufzeitkonfiguration

Visual Studio für Mac ermöglicht es Ihnen, eine _Laufzeitkonfiguration_ festzulegen. Die Laufzeitkonfigurationen werden in einer Dropdownliste in der Symbolleiste neben dem Buildkonfigurationsselektor aufgelistet, wie unten veranschaulicht:

![Dropdownmenü Laufzeitkonfiguration](media/projects-and-solutions-image8.png)

Eine Laufzeitkonfiguration ist ein Satz von Ausführungsoptionen mit einem Namen und mehreren Konfigurationen, die in einem Projekt zu verschiedenen Zwecken definiert sind. Laufzeitkonfigurationen werden auf Ebene des Projekts definiert. Für jedes ausführbare Projekt wird automatisch ein Standard erstellt – Sie können aber so viele wie nötig hinzufügen. Bestimmte Projekttypen generieren automatisch zusätzliche Laufzeitkonfigurationen. watchOS-Projekte können z.B. _Übersichts- und Benachrichtigungskonfigurationen_ generieren.

Konfigurationen können für andere Entwickler freigegeben (in diesem Fall werden die Konfigurationen in der CSPROJ-Datei gespeichert) oder lokal gespeichert werden (in diesem Fall werden sie in einer USER-Datei gespeichert).

### <a name="android-run-configurations"></a>Android-Laufzeitkonfigurationen

Mit Laufzeitkonfigurationen für Android-Projekte können Sie einen bestimmten Empfänger für eine Aktivität, einen Dienst oder Übertragungen festlegen, der gestartet werden soll, wenn Sie ein Projekt ausführen oder debuggen. Sie können beabsichtigte zusätzliche Daten übergeben und beabsichtigte Flags festlegen, um Ihre Komponenten unter anderen Startbedingungen zu testen.

Für Aktivitäten, die nicht `MainLauncher` sind, muss `Exported=true` dem Aktivitätsattribut zum Debuggen auf einem physischen Gerät hinzugefügt werden, oder der Filter „Beabsichtigt“ muss definiert sein.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Beispiele für Daten, die möglicherweise in Laufzeitkonfigurationen eingeschlossen werden

Die folgende Liste enthält Beispiele für Daten, die in Laufzeitkonfigurationen eingeschlossen werden könnten:

* Normales .NET-Projekt
  * Alternative Start-App
  * Startargumente
  * Arbeitsverzeichnis
  * Umgebungsvariablen
  * Mono-Laufzeitoptionen (nur unter Mono verwenden)
* Android-Projekt
  * Einstiegspunkt (Aktivität, Dienst, Empfänger)
  * Beabsichtigte Argumente und Daten
* iOS-Projekt
  * Modus (Normal, Abrufen im Hintergrund)
* iOS-Erweiterungsprojekt
  * Start-App: Standard oder benutzerdefiniert
* WatchKit-Projekt
  * Modus (Übersicht, Benachrichtigung)
  * Benachrichtigungsplayload

## <a name="see-also"></a>Weitere Informationen

- [Grundlagen der Buildkonfiguration (Visual Studio unter Windows)](/visualstudio/ide/understanding-build-configurations)

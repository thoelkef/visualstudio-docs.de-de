---
title: Grundlagen der Buildkonfiguration in Visual Studio für Mac
description: In diesem Artikel erfahren Sie mehr über die verschiedenen Buildkonfigurationen in Visual Studio für Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: b0ab3786f9bbb713fdc2b4726b29148c4bcd9f34
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="understanding-build-configurations"></a>Grundlagen der Buildkonfiguration

## <a name="project-build-configurations"></a>Projektbuildkonfigurationen 

Projekte haben tendenziell mehrere Konfigurationen. Wenn Sie zwischen diesen wechseln, erhalten Sie zur Buildzeit unterschiedliche Ausgaben. Eine Debugkonfiguration gibt z.B. Debuggingsymbole aus, mit denen der Debugger Funktionsnamen, Parameter oder Variablen aus der Stapelüberwachung einer abgestürzten Anwendung auflösen kann. Diese zusätzlichen Informationen sind zwar während der Entwicklung nützlich, blähen die Datei jedoch auf und sind für die Verteilung nicht ideal.

Jede Plattform hat spezifische Konfigurationen für ihre Builds. 

## <a name="solution-configurations"></a>Projektmappenkonfigurationen

Ähnlich wie Projektkonfigurationen werden Projektmappenkonfigurationen verwendet, um benutzerdefinierte Konfigurationen für ein gesamtes Projekt zu erstellen. Über die Registerkarte **Konfigurationszuordnungen** unter **Build > Konfigurationen** können Sie eine Zielkonfiguration für jedes Projektmappenelement zuweisen, wie in der folgenden Abbildung dargestellt:


 ![Optionen Konfigurationszuordnung](media/projects-and-solutions-image3.png)

Weitere Informationen über Konfigurationen finden Sie in dem Video zum [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) von James Montemagno.

## <a name="run-configuration"></a>Laufzeitkonfiguration

In vorherigen Versionen von Xamarin Studio konnten Sie ein Projekt als **Startprojekt** festlegen. Dabei handelt es sich um das Projekt, das ausgeführt bzw. debuggt wird, wenn Sie den globalen Befehl „Ausführen/Debuggen“ verwenden. Der Name des Startprojekts wurde im Projektpad fett geschrieben.

Statt ein Startprojekt festzulegen, können Sie in Visual Studio für Mac eine _Laufzeitkonfiguration_ festlegen. Die Laufzeitkonfigurationen werden in einer Dropdownliste in der Symbolleiste neben dem Buildkonfigurationsselektor aufgelistet, wie unten veranschaulicht:

 ![Dropdownmenü Laufzeitkonfiguration](media/projects-and-solutions-image8.png)

Eine Laufzeitkonfiguration ist ein Satz von Ausführungsoptionen mit einem Namen und mehreren Konfigurationen, die in einem Projekt zu verschiedenen Zwecken definiert sind. Lauftzeitkonfigurationen werden auf Ebene des Projekts definiert. Für jedes ausführbare Projekt wird automatisch ein Standard erstellt – Sie können aber so viele wie nötig hinzufügen. Bestimmte Projekttypen generieren automatisch zusätzliche Laufzeitkonfigurationen. watchOS-Projekte können z.B. _Übersichts- und Benachrichtigungskonfigurationen_ generieren. 
 
Konfigurationen können für andere Entwickler freigegeben (in diesem Fall werden die Konfigurationen in der CSPROJ-Datei gespeichert) oder lokal gespeichert werden (in diesem Fall werden Sie in einer USER-Datei gespeichert).

### <a name="android-run-configurations"></a>Android-Laufzeitkonfigurationen
 
Mit Laufzeitkonfigurationen für Android-Projekte können Sie festlegen, welcher Empfänger von Aktivitäten, Diensten und Übertragungen gestartet werden soll, wenn Sie ein Projekt ausführen oder debuggen. Sie können beabsichtigte zusätzliche Daten übergeben und beabsichtigte Flags festlegen, um Ihre Komponenten unter anderen Startbedingungen zu testen.

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

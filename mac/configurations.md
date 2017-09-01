---
title: Grundlagen der Buildkonfiguration
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: e435418c0c77f1577e9db8ab35d76d6bd54f8447
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---

# <a name="understanding-build-configurations"></a>Grundlagen der Buildkonfiguration

## <a name="project-build-configurations"></a>Projektbuildkonfigurationen 

Projekte können mehrere Konfigurationen haben. Wenn Sie zwischen diesen Wechseln, erhalten Sie zur Buildzeit unterschiedliche Ausgaben. Wenn sie z.B eine Debugkonfiguration verwenden, enthält die Ausgabe Debuggingsymbole, mit denen der Debugger Funktionsnamen, Parameter oder Variablen aus der Stapelüberwachung einer abgestürzten Anwendung auflösen kann. Wenn Sie eine Debugkonfiguration verwenden, führt dies jedoch zu einer erhöhten Dateigröße, was für eine Anwendung, die verteilt werden soll, nicht ideal ist.

Jede Plattform hat spezifische Konfigurationen für ihre Builds. Die Xamarin.Android-Entwicklung wird immer nur eine Release- und eine Debugkonfiguration haben. Xamarin.iOS verfügt über mehr Konfigurationen. Neuere iOS-Projekte haben nur Debug- oder Releasekonfigurationen. Diese können jedoch für ein Gerät oder einen installierten Simulator festgelegt werden.

## <a name="solution-configurations"></a>Projektmappenkonfigurationen

Ähnlich wie Projektkonfigurationen werden Projektmappenkonfigurationen verwendet, um benutzerdefinierte Konfigurationen für ein gesamtes Projekt zu erstellen. Über die Registerkarte **Konfigurationszuordnungen** unter **Build > Konfigurationen** können Sie eine Zielkonfiguration für jedes Projektmappenelement zuweisen, wie unten veranschaulicht:


 ![Optionen Konfigurationszuordnung](media/projects-and-solutions-image3.png)

Weitere Informationen finden Sie in dem Video zum [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) von James Montemagno (in englischer Sprache).

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

Die unten stehende Liste enthält Beispiel für Daten, die in Laufzeitkonfigurationen eingeschlossen werden könnten:

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


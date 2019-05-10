---
title: Schreiben und Debuggen von XAML mit XAML "Hot" neu laden
description: Laden von XAML "Hot" oder XAML bearbeiten und fortfahren, können Sie Änderungen an Ihrem XAML-Code vornehmen, während der Ausführung von apps
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a002c3876eecf0f31a8d104fa235b1208af90699
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929131"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Schreiben und Debuggen von ausgeführten XAML-Code mit "Hot" Laden von XAML in Visual Studio

Visual Studio-XAML "Hot" erneut laden, können Sie Ihre WPF- oder UWP-app UI erstellen, und lassen Sie die Änderungen in XAML-Code vornehmen, während Ihre app ausgeführt wird. Dieses Feature können Sie inkrementell erstellen und Testen XAML-Code mit dem Vorteil der Datenkontext für die ausgeführte app Authentifizierungsstatus und andere realen-Komplexität, die schwer zu simulieren, während der Entwurfsphase ist.

XAML "Hot" erneut laden ist besonders hilfreich, in diesen Szenarien:

* Beheben von Problemen mit Benutzeroberfläche finden Sie in Ihren XAML-Code, nachdem die app im Debugmodus gestartet wurde.

* Erstellen einer neuen UI-Komponente für eine app, ist in der Entwicklung, profitieren Sie von Ihrer app-Runtime-Kontext.

|Unterstützte Anwendungstypen|Betriebssystem und Tools|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+</br>Windows 7 und höher |
|Universelle Windows-apps (UWP)|Windows 10 und höher, mit der [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Visual Studio XAML "Hot" erneut laden ist derzeit nur unterstützt, wenn Ihre Anwendung in Visual Studio mit dem angefügten Debugger ausführen (**F5** oder **Debuggen**). Sie können nicht über diese Oberfläche aktivieren *an den Prozess anhängen*.

## <a name="known-limitations"></a>Bekannte Einschränkungen

Im folgenden werden bekannte Einschränkungen von XAML die erneut laden "Hot". Um Einschränkung zu umgehen, die auftreten, beenden Sie den Debugger nur aus, und schließen Sie dann den Vorgang.

|Einschränkung|WPF|UWP|Hinweise|
|-|-|-|-|
|Verknüpfen von Ereignissen mit Steuerelementen, während die app ausgeführt wird|Nicht unterstützt|Nicht unterstützt|Fehler angezeigt: *Stellen Sie sicher Ereignis Fehler*|
|Erstellen Ressourcenobjekte in einem Ressourcenwörterbuch, z. B. in Ihrer app Seitenfenster oder *"App.xaml"*|Nicht unterstützt|Unterstützt|Beispiel: Hinzufügen einer ```SolidColorBrush``` in ein Ressourcenverzeichnis für die Verwendung als eine ```StaticResource```.</br>Hinweis: Statische Ressourcen, Stil-Konverter und andere Elemente in einem Ressourcenverzeichnis geschrieben können angewendet/verwendet werden, bei der Verwendung von XAML "Hot" erneut laden. Nur die Erstellung der Ressource wird nicht unterstützt.</br> Ändern das Ressourcenverzeichnis ```Source``` Eigenschaft.| 
|Neue Steuerelemente, Klassen, Windows oder andere Dateien hinzufügen zum Projekt, während die app ausgeführt wird|Nicht unterstützt|Nicht unterstützt|Keiner|
|Verwalten von NuGet-Pakete (Pakete hinzufügen/entfernen/aktualisieren)|Nicht unterstützt|Nicht unterstützt|Keiner|
|Ändern von Daten, die Bindung, verwendet die {X: Bind}-Markuperweiterung|Nicht zutreffend|In Visual Studio-2019 und höheren Versionen unterstützt|In Visual Studio 2018 oder früheren Versionen unterstützt nicht|

## <a name="error-messages"></a>Fehlermeldungen

Möglicherweise stoßen Sie auf die folgenden Fehler bei der Verwendung von XAML "Hot" neu laden.

|Fehlermeldung|Beschreibung|
|-|-|-|
|Stellen Sie sicher Ereignis Fehler|Fehler weist darauf hin, dass Sie versuchen, ein Ereignis zu verknüpfen, um eines der Steuerelemente, die während der Ausführung Ihrer Anwendung nicht unterstützt wird.|
|Die XAML-Funktion „Bearbeiten und Fortfahren“ hat keine Elemente für die Aktualisierung gefunden.|Fehler tritt auf, beim Bearbeiten von XAML, die Speicherebenen "Hot" Laden in Ihrer app nicht aktualisieren kann.</br> In einigen Fällen kann dieser Fehler behoben werden, mit der ausgeführten app um zu einer Ansicht zu navigieren, in der XAML verwendet wird.</br> In manchen Fällen bedeutet dieser Fehler an, dass die Änderung nicht angewendet werden kann, bis Sie die Debugsitzung neu starten. |
|Diese Änderung wird während einer Debugsitzung nicht unterstützt.|Fehler weist darauf hin, dass die Änderung, die Sie versuchen, die nicht von "Hot" Reload XAML unterstützt wird. Beenden Sie die Debugsitzung, nehmen Sie die Änderung, und klicken Sie dann starten Sie die Debugsitzung neu.|
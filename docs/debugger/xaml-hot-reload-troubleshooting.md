---
title: Problembehandlung bei XAML Hot Neuladen
description: Beheben Sie Probleme, die beim erneuten Laden von XAML auftreten können.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbfb88113eec35dec72d5c3753dc37775a7a2591
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988176"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Problembehandlung bei XAML Hot Neuladen

Dieses Handbuch zur Problembehandlung umfasst ausführliche Anweisungen, mit denen die meisten Probleme gelöst werden, die verhindern, dass XAML Hot-Neuladen ordnungsgemäß

Das Laden von XAML-Hot wird für WPF-und UWP-Apps unterstützt. Ausführliche Informationen zu den Anforderungen an das Betriebssystem und die Tools finden Sie unter [schreiben und Debuggen von XAML-Code mit XAML Hot Neuladen](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Das heiße laden ist nicht verfügbar.

Wenn beim Debuggen Ihrer APP die Meldung "das Laden ist nicht verfügbar" in der Symbolleiste in der App angezeigt wird, befolgen Sie die Anweisungen in diesem Artikel, um das Problem zu beheben.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Überprüfen, ob das aktive XAML-laden aktiviert ist

Die Funktion ist standardmäßig aktiviert. Wenn Sie mit dem Debuggen Ihrer APP beginnen, sollten Sie sicherstellen, dass die in-App-Symbolleiste angezeigt wird, die bestätigt, dass das Laden von XAML Hot

![XAML-Hot-Upload verfügbar](../debugger/media/xaml-hot-reload-available.png)

Wenn die in-App-Symbolleiste nicht angezeigt wird, öffnen Sie >  **Debugoptionen** > **Allgemein**. Stellen Sie sicher, dass beide Optionen **UI-Debuggingtools für XAML aktivieren** und **XAML-Hot-Neuladen aktivieren** ausgewählt sind.

![XAML-Hot-Upload aktivieren](../debugger/media/xaml-hot-reload-enable.png)

Wenn diese Optionen ausgewählt sind, wechseln Sie zu Live Visual Tree (**Debuggen** > Sie**Windows** > **Live Visual Tree**), und vergewissern Sie sich, dass die Schaltfläche **Lauf Zeit Tools in der Anwendungs** Symbolleiste anzeigen (ganz links) ausgewählt ist.

![XAML-Hot-Upload aktivieren](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Vergewissern Sie sich, dass Sie Debuggen statt an den Prozess anhängen verwenden.

XAML Hot Neuladen erfordert, dass die `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` Umgebungsvariable zum Zeitpunkt des Starts der Anwendung auf 1 festgelegt ist. Visual Studio legt dies automatisch als **Teil des** > Befehls**Debuggen Debuggen starten** (oder **F5**) fest. Wenn Sie XAML Hot Upload mit dem Befehl **Debuggen** > **an den Prozess anhängen** verwenden möchten, legen Sie die Umgebungsvariable selbst fest.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Überprüfen Sie, ob die MSBuild-Eigenschaften richtig sind

Standardmäßig sind Quell Informationen in einer Debugkonfiguration enthalten. Sie wird von MSBuild-Eigenschaften in ihren Projektdateien (z. b. *. csproj) gesteuert. Für WPF ist `XamlDebuggingInformation`die-Eigenschaft, die auf `True`festgelegt werden muss. Bei UWP ist `DisableXbfLineInfo`die-Eigenschaft, die auf `False`festgelegt werden muss. Beispiel:

WPF

`<XamlDebuggingInformation>True</XamlDebuggingInformation>` 

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Vergewissern Sie sich, dass Sie den richtigen Buildkonfigurationsnamen verwenden.

Sie müssen entweder die korrekte MSBuild-Eigenschaft manuell festlegen, um das Laden von XAML Hot (siehe vorheriger Abschnitt) zu unterstützen, oder Sie müssen den standardbuildkonfigurationsnamen (Debug) verwenden. Wenn Sie die MSBuild-Eigenschaft nicht ordnungsgemäß festlegen, funktioniert ein benutzerdefinierter buildkonfigurationsname weder, noch wird ein Releasebuild ausgeführt.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Überprüfen Sie, ob die XAML-Datei keine Fehler aufweist.

Wenn die XAML-Datei Fehler im **Fehlerliste**anzeigt, funktioniert das Laden von XAML-Hot möglicherweise nicht.

## <a name="see-also"></a>Siehe auch

[Schreiben und Debuggen von XAML-Code mit XAML Hot Neuladen](xaml-hot-reload.md)

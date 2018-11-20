---
title: Was bedeutet „Debuggen“?
description: Verstehen Sie, was es bedeutet, eine app zu debuggen
ms.custom: debug-experiments
ms.date: 10/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7cd96d61718972c82c6002888e123003530c019c
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826660"
---
# <a name="what-is-debugging"></a>Was bedeutet „Debuggen“?

Visual Studio-Debugger ist ein leistungsfähiges Tool. Bevor wir, wie sie verwendet werden, möchten wir einige Begriffe wie z. B. sprechen *Debugger*, *Debuggen*, und *Debugmodus*. Auf diese Weise, wenn wir später sprechen, zu suchen und Beheben von Fehlern, werden wir das gleiche sprechen werden.

## <a name="debugger-vs-debugging"></a>Debugger-im Vergleich zu debuggen

Der Begriff *Debuggen* ist sehr allgemein und kann eine Menge verschiedener Dinge bedeuten. In der die Literale Verwendung des Worts bedeutet dies einen Fehler aus dem Code entfernen. Nun, es gibt viele Möglichkeiten zur Verfügung. Sie können z. B. durch das Scannen des Codes, der nach Tippfehlern oder mithilfe eines codeanalyzers Debuggen. Sie können den Code Debuggen, mithilfe einer Leistungsanalyse. Oder Sie können mit Debuggen einer *Debugger*.

Ein Debugger ist eine sehr spezielle Entwicklungstool. Ein Debugger an der ausgeführten app angefügt und ermöglicht es Ihnen, Ihren Code zu überprüfen. In der debugging-Dokumentation für Visual Studio ist dies i. d. r. was wir meinen, wenn wir sagen "Debuggen".

## <a name="debug-mode-vs-running-your-app"></a>Debug-Modus im Vergleich zu die app ausgeführt wird

Wenn Sie Ihre app in Visual Studio zum ersten Mal ausführen, können Sie ihn starten, durch Drücken der Schaltfläche mit dem grünen Pfeil ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debuggen starten") auf der Symbolleiste. In der Standardeinstellung die **Debuggen** Wert wird in der Dropdownliste auf der linken Seite angezeigt. Wenn Sie Visual Studio vertraut sind, lassen dies den Eindruck, dass das Debuggen Ihrer app mit Ausführung geschehen kann Ihre app – die It ist –, aber Hierbei handelt es sich im Grunde zwei sehr unterschiedlichen Aufgaben.

![Wählen Sie einen Debugbuild](../debugger/media/what-is-debugging-debug-build.png)

Ein **Debuggen** Wert gibt an, eine Debug-Konfiguration. Beim Starten der app (drücken Sie den grünen Pfeil oder **F5**) in einer Konfiguration Debuggen, starten Sie die app im *Debugmodus*, d. h. Sie Ihre app mit einem angefügten Debugger ausführen. Dies ermöglicht es sich um einen vollständigen Satz von Debugfunktionen, die Sie verwenden können, um Fehler in Ihrer app zu finden.

Wenn Sie ein Projekt geöffnet haben, wählen Sie es in den Bereich der Dropdownauswahl **Debuggen** , und wählen Sie **Version** stattdessen.

![Wählen Sie einen Releasebuild](../debugger/media/what-is-debugging-release-build.png)

Wenn Sie diese Einstellung wechseln, ändern Sie das Projekt aus einer Debugkonfiguration in einer Releasekonfiguration. Visual Studio-Projekte verfügen über separate Release- und Debugkonfigurationen für Ihr Programm. Sie erstellen die Debugversion zum Debuggen und die Releaseversion für die endgültige Version. Ein Releasebuild für Leistung optimiert ist, aber ein Debugbuild ist besser für das Debuggen.

## <a name="when-to-use-a-debugger"></a>Beim Verwenden eines Debuggers

Der Debugger ist ein wichtiges Tool zum Suchen und Beheben von Fehlern in Ihren apps. Allerdings ist entscheidend, Kontext, und es ist wichtig, nutzen Sie alle Tools stehen zu Ihrer verwerfbare Objekt können Sie schnell Fehler zu vermeiden. In einigen Fällen kann das Recht "Tool" besser Programmierstil sein. Erlernen den Debugger im Vergleich zu einem anderen Tool verwenden, erfahren Sie auch Gewusst wie: Verwenden Sie den Debugger effektiver. Wenn Sie bereits kennen müssen Sie den Debugger Informationen, finden Sie unter [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md). Führen Sie andernfalls den Link in **nächste Schritte**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, dass einige allgemeine Konzepte zum Debuggen. Als Nächstes können Sie beginnen, lernen, wie Sie mit Visual Studio zu debuggen und wie Sie Code mit weniger Fehlern schreiben. Der folgende Artikel zeigt C# Codebeispiele, die Konzepte gelten jedoch für alle Sprachen, die von Visual Studio unterstützt.

> [!div class="nextstepaction"]
> [Schreiben Sie besser C# code mithilfe von Visual Studio](../debugger/write-better-code-with-visual-studio.md)

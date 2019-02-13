---
title: Dialogfeld "Optionen", Projekte und Projektmappen, Erstellen und Ausführen
ms.date: 07/14/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2e62a0b9ece6052d222a8c228bbd7fe018b0a3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954776"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Dialogfeld "Optionen", Projekte und Projektmappen, Erstellen und Ausführen

In diesem Dialogfeld können Sie die maximale Anzahl von Visual C++- oder C#-Projekten, die gleichzeitig erstellt werden können, bestimmte standardmäßige Buildverhaltensweisen und einige Buildprotokolleinstellungen angeben. Wählen Sie zum Zugriff auf diese Optionen **Extras > Optionen** aus, erweitern Sie **Projekte und Projektmappen**, und wählen Sie **Erstellen und Ausführen** aus.

**Maximale Anzahl paralleler Projektbuilds**

Gibt die maximale Anzahl von Visual C++- und C#-Projekten an, die gleichzeitig erstellt werden können. Zur Optimierung des Buildvorgangs wird die maximale Anzahl paralleler Projektbuilds automatisch auf die Anzahl der CPUs des Computers festgelegt. Die maximale Anzahl beträgt 32.

**Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**

Es werden nur das Startprojekt und dessen Abhängigkeiten erstellt, wenn Sie auf F5 drücken, den Menübefehl **Debuggen > Starten** oder zutreffende Befehle auf dem Menü **Erstellen** auswählen. Wenn aktiviert, werden alle Projekte und Abhängigkeiten erstellt.

**Beim Ausführen, bei nicht aktuellen Projekten**

*Dies bezieht sich nur auf [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Projekte.*

Wenn Sie ein Projekt mit F5 oder dem Befehl **Debuggen > Starten** ausführen, zeigt die Standardeinstellung **Zum Erstellen auffordern** eine Meldung an, wenn eine Projektkonfiguration veraltet ist. Wählen Sie **Immer erstellen** aus, um das Projekt jedes Mal bei Ausführung zu erstellen. Wählen Sie **Nie erstellen** aus, um alle automatischen Builds zu unterdrücken, wenn das Projekt ausgeführt wird.

**Beim Ausführen, bei Build- oder Bereitstellungsfehlern**

*Dies bezieht sich nur auf [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Projekte.*

Wenn Sie ein Projekt mit F5 oder dem Befehl **Debuggen > Starten** ausführen, zeigt die Standardeinstellung **Zum Starten auffordern** eine Meldung an, wenn ein Projekt ausgeführt werden soll, auch wenn der Build fehlgeschlagen ist. Wählen Sie **Alte Version starten** aus, um automatisch den letzten guten Build zu starten, was zu Konflikten zwischen dem aufgeführten Code und dem Quellcode führen könnte. Wählen Sie **Nicht starten** aus, um die Meldung zu unterdrücken.

**Aktuell ausgewähltes Projekt als Startprojekt für neue Projektmappen verwenden**

Wenn diese Option festgelegt ist, verwenden neue Projektmappen das aktuell ausgewählten Projekt als Startprojekt.

**Ausführlichkeit der MSBuild-Projektbuildausgabe**

Bestimmt, wie viele Informationen im Fenster **Ausgabe** für den Build angezeigt werden.

**Ausführlichkeit der Protokolldatei des MSBuild-Projektbuilds**

*Dies bezieht sich nur auf [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Projekte.*

Bestimmt, wie viele Informationen in die Buildprotokolldatei geschrieben werden, die sich unter „\\...\\*ProjectName*\Debug\\*ProjectName*.log.

## <a name="see-also"></a>Siehe auch

- [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)
- [Optionen (Dialogfeld), Projekte und Projektmappen](projects-and-solutions-options-dialog-box.md)
- [Dialogfeld „Optionen“, Projekte und Projektmappen, Webprojekte](options-dialog-box-projects-and-solutions-web-projects.md)
---
title: "Dialogfeld \" Optionen\", Projekte und Projektmappen, Erstellen und Ausführen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 88f3ec2d9e8c682511c87cbcf5a5690ae797d8c7
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen

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
[Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)  
[Optionen (Dialogfeld), Projekte und Projektmappen](projects-and-solutions-options-dialog-box.md)  
[Dialogfeld „Optionen“, Projekte und Projektmappen, Webprojekte](options-dialog-box-projects-and-solutions-web-projects.md)
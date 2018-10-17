---
title: Dialogfeld " Optionen", Projekte und Projektmappen, Erstellen und Ausführen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9669437ff47bc141c898a61c055b3a0de8d5d235
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189292"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
In diesem Dialogfeld können Sie die maximale Anzahl von Visual C++- oder Visual C#-Projekten, die gleichzeitig erstellt werden können, bestimmte standardmäßige Buildverhaltensweisen und einige Protokolleinstellungen angeben. Zum Öffnen der **Optionen** Dialogfeld wählen **Tools**, **Optionen** in der Menüleiste. Um diese Optionen zuzugreifen, erweitern Sie **Projekte und Projektmappen**, und wählen Sie dann **erstellen und ausführen**.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Maximale Anzahl paralleler Projektbuilds**  
 Gibt die maximale Anzahl von Visual C++- und Visual C#-Projekten an, die gleichzeitig erstellt werden können. Zur Optimierung des Buildvorgangs wird die maximale Anzahl paralleler Projektbuilds automatisch auf die Anzahl der CPUs des Computers festgelegt. Die maximale Anzahl beträgt 32.  
  
 **Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**  
 Nur das Startprojekt und seine Abhängigkeiten sind integriert, wenn dieses Kontrollkästchen aktiviert ist, wenn Sie die F5-Taste auswählen. Wählen Sie **Debuggen**, **starten** im Menü Leiste, oder wählen Sie **erstellen**, **erstellen** in der Menüleiste. Wenn dieses Kontrollkästchen deaktiviert ist, wenn Sie die F5-Taste drücken, werden alle Projekte, Abhängigkeiten und Lösungsdateien erstellt; Wählen Sie **Debuggen**, **starten** im Menü Leiste, oder wählen Sie **erstellen**, **erstellen** in der Menüleiste. Diese Option ist standardmäßig deaktiviert.  
  
 **Beim Ausführen, bei nicht aktuellen Projekten**  
 > [!NOTE]
>  Diese Liste gilt nur für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekte.  
  
 Standardmäßig wird eine Meldung angezeigt, wenn eine Projektkonfiguration veraltet ist, wenn Sie drücken die Taste F5 oder wählen Sie **Debuggen**, **starten** in der Menüleiste. Sie können angeben, ob das Projekt trotzdem erstellt werden soll und ob die Meldung angezeigt wird. Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird, und wie das Buildverhalten sein soll, wenn die Meldung nicht angezeigt wird.  
  
 **Immer erstellen**  
 Das Meldungsfeld wird nicht angezeigt, und das Projekt wird trotz der veralteten Konfiguration erstellt. Diese Option wird festgelegt, bei der Auswahl der **dieses Dialogfeld nicht mehr anzeigen** Feld in der Nachricht, und wählen Sie dann die **Ja** Schaltfläche.  
  
 **Nie erstellen**  
 Das Meldungsfeld wird nicht angezeigt, und das Projekt wird nicht erstellt. Diese Option wird festgelegt, bei der Auswahl der **dieses Dialogfeld nicht mehr anzeigen** Feld in der Nachricht, und wählen Sie dann die **keine** Schaltfläche.  
  
 **Zum Erstellen auffordern**  
 Zeigt das Meldungsfeld jedes Mal an, wenn eine Projektkonfiguration veraltet ist.  
  
 **Beim Ausführen, bei Build- oder Bereitstellungsfehlern**  
 Wenn Buildfehler auftreten, wenn Sie einen Build aus starten die **erstellen** Menü wird eine Meldung angezeigt. Sie können angeben, ob Sie mit dem Starten der Anwendung fortfahren möchten und ob die Nachricht jedes Mal angezeigt wird, wenn diese Buildfehler auftreten. Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird und wie das Verhalten sein soll, wenn die Meldung nicht angezeigt wird.  
  
> [!NOTE]
>  Diese Option gilt nur für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekte.  
  
 **Zum Starten auffordern**  
 Zeigt jedes Mal ein Meldungsfeld an, wenn diese Buildfehler auftreten.  
  
 **Nicht starten**  
 Das Meldungsfeld wird nicht angezeigt, und die Anwendung wird nicht gestartet. Diese Option wird festgelegt, bei der Auswahl der **dieses Dialogfeld nicht mehr anzeigen** Kontrollkästchen in der MessageBox, und wählen Sie dann die **keine** Schaltfläche.  
  
 **Alte Version starten**  
 Das Meldungsfeld wird nicht angezeigt, und die neu erstellte Version der Anwendung wird nicht gestartet. Diese Option wird festgelegt, bei der Auswahl der **dieses Dialogfeld nicht mehr anzeigen** Kontrollkästchen in der MessageBox, und wählen Sie dann die **Ja** Schaltfläche.  
  
 **Aktuell ausgewähltes Projekt als Startprojekt für neue Projektmappen verwenden**  
 Wenn dieses Kontrollkästchen aktiviert ist, verwenden neue Projektmappen das aktuell ausgewählte Projekt als Startprojekt.  
  
 **Ausführlichkeit der MSBuild-Projektbuildausgabe**  
 Bestimmt, wie viele Informationen im Fenster **Ausgabe** für den Build angezeigt werden.  
  
 **Ausführlichkeit der Protokolldatei des MSBuild-Projektbuilds**  
 > [!NOTE]
>  Diese Option gilt nur für Visual C++-Projekte.  
  
 Bestimmt, wie viele Informationen in die Buildprotokolldatei geschrieben werden, die sich unter „\\...\\*ProjectName*\Debug\\*ProjectName*.log.  
  
## <a name="see-also"></a>Siehe auch  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)




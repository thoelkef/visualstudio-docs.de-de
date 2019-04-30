---
title: Dialogfeld " Optionen", Projekte und Projektmappen, Erstellen und Ausführen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: a0ce02a76d32a967e2c7e5f06818b5838337f9b1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433679"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die maximale Anzahl von Visual C++- oder Visual C#-Projekten, die gleichzeitig erstellt werden können, bestimmte standardmäßige Buildverhaltensweisen und einige Protokolleinstellungen angeben. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen. Sie können auf diese Optionen zugreifen, indem Sie **Projekte und Projektmappen** erweitern und dann **Erstellen und Ausführen** auswählen.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Maximale Anzahl paralleler Projektbuilds**  
 Gibt die maximale Anzahl von Visual C++- und Visual C#-Projekten an, die gleichzeitig erstellt werden können. Zur Optimierung des Buildvorgangs wird die maximale Anzahl paralleler Projektbuilds automatisch auf die Anzahl der CPUs des Computers festgelegt. Die maximale Anzahl beträgt 32.  
  
 **Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**  
 Wenn dieses Kontrollkästchen aktiviert ist und Sie F5 drücken bzw. **Debuggen** > **Start** oder **Erstellen** > **Erstellen** in der Menüleiste auswählen, werden nur das Startprojekt und dessen Abhängigkeiten erstellt. Wenn dieses Kontrollkästchen deaktiviert ist und Sie F5 drücken bzw. **Debuggen** > **Start** oder **Erstellen** > **Erstellen** in der Menüleiste auswählen, werden alle Projekte, Abhängigkeiten und Projektmappendateien erstellt. Diese Option ist standardmäßig deaktiviert.  
  
 **Beim Ausführen, bei nicht aktuellen Projekten**  
 > [!NOTE]
> Diese Liste gilt nur für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekte.  
  
 In der Standardeinstellung wird eine Meldung angezeigt, wenn eine Projektkonfiguration veraltet ist, wenn Sie die F5-Taste drücken oder **Debuggen** > **Start** in der Menüleiste auswählen. Sie können angeben, ob das Projekt trotzdem erstellt werden soll und ob die Meldung angezeigt wird. Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird, und wie das Buildverhalten sein soll, wenn die Meldung nicht angezeigt wird.  
  
 **Immer erstellen**  
 Das Meldungsfeld wird nicht angezeigt, und das Projekt wird trotz der veralteten Konfiguration erstellt. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** in der Nachricht aktivieren und dann auf **Ja** klicken.  
  
 **Nie erstellen**  
 Das Meldungsfeld wird nicht angezeigt, und das Projekt wird nicht erstellt. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** in der Nachricht aktivieren und dann auf **Nein** klicken.  
  
 **Zum Erstellen auffordern**  
 Zeigt das Meldungsfeld jedes Mal an, wenn eine Projektkonfiguration veraltet ist.  
  
 **Beim Ausführen, bei Build- oder Bereitstellungsfehlern**  
 Wenn Buildfehler beim Start eines Builds über das Menü **Erstellen** auftreten, wird eine Meldung angezeigt. Sie können angeben, ob Sie mit dem Starten der Anwendung fortfahren möchten und ob die Nachricht jedes Mal angezeigt wird, wenn diese Buildfehler auftreten. Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird und wie das Verhalten sein soll, wenn die Meldung nicht angezeigt wird.  
  
> [!NOTE]
> Diese Option gilt nur für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekte.  
  
 **Zum Starten auffordern**  
 Zeigt jedes Mal ein Meldungsfeld an, wenn diese Buildfehler auftreten.  
  
 **Nicht starten**  
 Das Meldungsfeld wird nicht angezeigt, und die Anwendung wird nicht gestartet. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** im Nachrichtenfeld aktivieren und dann auf **Nein** klicken.  
  
 **Alte Version starten**  
 Das Meldungsfeld wird nicht angezeigt, und die neu erstellte Version der Anwendung wird nicht gestartet. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** im Nachrichtenfeld aktivieren und dann auf **Ja** klicken.  
  
 **Aktuell ausgewähltes Projekt als Startprojekt für neue Projektmappen verwenden**  
 Wenn dieses Kontrollkästchen aktiviert ist, verwenden neue Projektmappen das aktuell ausgewählte Projekt als Startprojekt.  
  
 **Ausführlichkeit der MSBuild-Projektbuildausgabe**  
 Bestimmt, wie viele Informationen im Fenster **Ausgabe** für den Build angezeigt werden.  
  
 **Ausführlichkeit der Protokolldatei des MSBuild-Projektbuilds**  
 > [!NOTE]
> Diese Option gilt nur für Visual C++-Projekte.  
  
 Bestimmt, wie viele Informationen in die Buildprotokolldatei geschrieben werden, die sich unter „\\...\\*ProjectName*\Debug\\*ProjectName*.log.  
  
## <a name="see-also"></a>Siehe auch  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)

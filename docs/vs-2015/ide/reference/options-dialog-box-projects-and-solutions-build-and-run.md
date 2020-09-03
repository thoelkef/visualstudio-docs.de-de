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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655186"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die maximale Anzahl von Visual C++- oder Visual C#-Projekten, die gleichzeitig erstellt werden können, bestimmte standardmäßige Buildverhaltensweisen und einige Protokolleinstellungen angeben. Klicken Sie in der Menüleiste auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen. Sie können auf diese Optionen zugreifen, indem Sie **Projekte und Projektmappen** erweitern und dann **Erstellen und Ausführen** auswählen.

## <a name="uielement-list"></a>UIElement-Liste
 **Maximale Anzahl paralleler Projektbuilds** Gibt die maximale Anzahl von Visual C++-und Visual c#-Projekten an, die gleichzeitig erstellt werden können. Zur Optimierung des Buildvorgangs wird die maximale Anzahl paralleler Projektbuilds automatisch auf die Anzahl der CPUs des Computers festgelegt. Der maximale Wert beträgt 32.

 **Nur Start Projekte und Abhängigkeiten zur Laufzeit erstellen** Wenn dieses Kontrollkästchen aktiviert ist, werden nur das Startprojekt und seine Abhängigkeiten erstellt, wenn Sie die F5-Taste drücken. Wählen Sie **Debuggen**, **starten** in der Menüleiste aus. oder wählen Sie **Erstellen**, **Erstellen** in der Menüleiste aus. Wenn dieses Kontrollkästchen deaktiviert ist und Sie F5 drücken bzw. **Debuggen** > **Start** oder **Erstellen** > **Erstellen** in der Menüleiste auswählen, werden alle Projekte, Abhängigkeiten und Projektmappendateien erstellt. Diese Option ist standardmäßig deaktiviert.

 **Beim Ausführen, bei nicht aktuellen Projekten**
 > [!NOTE]
> Diese Liste gilt nur für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekte.

 In der Standardeinstellung wird eine Meldung angezeigt, wenn eine Projektkonfiguration veraltet ist, wenn Sie die F5-Taste drücken oder **Debuggen** > **Start** in der Menüleiste auswählen. Sie können angeben, ob das Projekt trotzdem erstellt werden soll und ob die Meldung angezeigt wird. Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird, und wie das Buildverhalten sein soll, wenn die Meldung nicht angezeigt wird.

 **Immer erstellen** Das Meldungs Feld wird nicht angezeigt, und das Projekt wird trotz der veralteten Konfiguration erstellt. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** in der Nachricht aktivieren und dann auf **Ja** klicken.

 **Nie erstellen** Das Meldungs Feld wird nicht angezeigt, und das Projekt wird nicht erstellt. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** in der Nachricht aktivieren und dann auf **Nein** klicken.

 **Zum Erstellen auffordern** Zeigt jedes Mal das Meldungs Feld an, wenn eine Projekt Konfiguration veraltet ist.

 **Beim Ausführen, wenn Build-oder Bereitstellungs Fehler auftreten** Wenn beim Starten eines Builds aus dem Menü **Erstellen** Buildfehler auftreten, wird eine Meldung angezeigt. Sie können angeben, ob Sie mit dem Starten der Anwendung fortfahren möchten und ob die Nachricht jedes Mal angezeigt wird, wenn diese Buildfehler auftreten. Verwenden Sie diese Option, um anzugeben, ob die Meldung angezeigt wird und wie das Verhalten sein soll, wenn die Meldung nicht angezeigt wird.

> [!NOTE]
> Diese Option gilt nur für [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekte.

 **Zum Starten auffordern** Zeigt jedes Mal ein Meldungs Feld an, wenn Buildfehler auftreten.

 **Nicht starten** Das Meldungs Feld wird nicht angezeigt, und die Anwendung wird nicht gestartet. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** im Nachrichtenfeld aktivieren und dann auf **Nein** klicken.

 **Alte Version starten** Das Meldungs Feld wird nicht angezeigt, und die neu erstellter Version der Anwendung wird nicht gestartet. Diese Option wird festgelegt, wenn Sie das Kontrollkästchen **Dieses Dialogfeld nicht mehr anzeigen** im Nachrichtenfeld aktivieren und dann auf **Ja** klicken.

 **Verwenden Sie für neue Projektmappen das aktuell ausgewählte Projekt als Startprojekt** . Wenn dieses Kontrollkästchen aktiviert ist, verwenden neue Projektmappen das aktuell ausgewählte Projekt als Startprojekt.

 **Ausführlichkeit der MSBuild-Projektbuildausgabe** Bestimmt, wie viele Informationen im Fenster **Ausgabe** für den Build angezeigt werden.

 **Ausführlichkeit der Protokolldatei des MSBuild-Projektbuilds**
 > [!NOTE]
> Diese Option gilt nur für Visual C++-Projekte.

 Bestimmt, wie viele Informationen in die Buildprotokollierung geschrieben werden, die sich unter \\ ... \\ *ProjectName*\Debug \\ *ProjectName*. log.

## <a name="see-also"></a>Weitere Informationen
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)

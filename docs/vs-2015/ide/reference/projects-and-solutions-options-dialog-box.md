---
title: Projekte und Projektmappen, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 245b453a3020e79b924cb8058ff392bd59673402
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662125"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projekte und Projektmappen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt den Standardpfad der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Projektordner fest und bestimmt das Standardverhalten der Fenster **Ausgabe**, **Aufgabenliste** und **Projektmappen-Explorer** bei der Entwicklung und Erstellung von Projekten. Klicken Sie zum Zugriff auf dieses Dialogfeld auf **Extras/Optionen**, erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.

> [!NOTE]
> Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Diese Hilfeseite wurde unter Berücksichtigung der Option **Allgemeine Entwicklungseinstellungen** verfasst. Klicken Sie im Menü **Tools** auf Einstellungen **Importieren und Exportieren**, um die Einstellungen anzuzeigen oder zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Einstellungen
 **Projekt Speicherort** Legt den Standard Speicherort fest, an dem neue Projekte und Projektmappenordner und Verzeichnisse erstellt werden. Verschiedene Dialogfelder verwenden auch den in dieser Option festgelegten Speicherort als Ausgangspunkt für Ordner. So verwendet z. B. das Dialogfeld "Projekt öffnen" diesen Speicherort für die Verknüpfung "Meine Projekte".

 **Speicherort von Benutzer Projektvorlagen** Legt den Standard Speicherort fest, der vom Dialogfeld **Neues Projekt** verwendet wird, um die Liste der **Vorlagen**zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Speicherort für Benutzer Element Vorlagen** Legt den Standard Speicherort fest, der im Dialogfeld **Neues Element hinzufügen** verwendet wird, um die Liste der **eigenen Vorlagen**zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Fehlerliste immer anzeigen, wenn der Build mit Fehlern abgeschlossen** wurde Öffnet das **Fehlerliste** Fenster beim Buildabschluss nur, wenn ein Projekt nicht erstellt werden konnte. Hier werden während des Buildvorgangs aufgetretene Fehler angezeigt. Wenn diese Option deaktiviert ist, treten die Fehler weiterhin auf, aber das Fenster wird nicht geöffnet, wenn der Build abgeschlossen ist. Diese Option ist standardmäßig aktiviert.

 **Aktives Element in Projektmappen-Explorer nachverfolgen** Wenn diese Option ausgewählt ist, wird **Projektmappen-Explorer** automatisch geöffnet, und das aktive Element ist ausgewählt. Das ausgewählte Element ändert sich beim Arbeiten mit unterschiedlichen Dateien in einem Projekt oder einer Projektmappe bzw. mit verschiedenen Komponenten in einem Designer. Wenn diese Option deaktiviert ist, ändert sich die Auswahl im **Projektmappen-Explorer** nicht automatisch. Diese Option ist standardmäßig aktiviert.

 **Erweiterte Buildkonfigurationen anzeigen** Wenn diese Option ausgewählt ist, werden die Optionen für die Buildkonfiguration im Dialogfeld **Eigenschaften Seiten für Projekt und Projekt** Mappen- **Eigenschaften Seiten** angezeigt. Wenn diese Option deaktiviert ist, werden die Optionen für die Buildkonfiguration nicht im Dialogfeld **Projekt-Eigenschaftenseiten** und **Projektmappen-Eigenschaftenseiten** für [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]- und [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Projekte angezeigt, die eine Konfiguration oder beide Konfigurationen (Debug und Release) enthalten. Wenn ein Projekt eine benutzerdefinierte Konfiguration hat, werden die Optionen für die Buildkonfiguration angezeigt.

 Wenn diese Option deaktiviert ist, werden die Befehle im Menü **Erstellen**, z.B. **Projektmappe erstellen**, **Projektmappe neu erstellen** und **Projektmappe bereinigen**, für die Releasekonfiguration ausgeführt, und die Befehle im Menü **Debuggen**, z.B. **Debuggen starten** und **Starten ohne Debugging**, werden für die Debugkonfiguration ausgeführt.

 Projekt Mappe **immer anzeigen** Wenn diese Option ausgewählt ist, werden die Projekt Mappe und alle Befehle, die auf Lösungen reagieren, immer in der IDE angezeigt. Wenn diese Option deaktiviert ist, werden alle Projekte als eigenständige Projekte erstellt, und Sie können die Projektmappe im Projektmappen-Explorer oder Befehle, die für Projektmappen ausgeführt werden, in der IDE nicht sehen, wenn die Projektmappe nur ein Projekt enthält.

 **Neue Projekte beim Erstellen speichern** Wenn Sie diese Option auswählen, können Sie einen Speicherort für das Projekt im Dialogfeld **Neues Projekt** angeben. Wenn diese Option deaktiviert ist, werden alle neuen Projekte als temporäre Projekte erstellt. Bei der Arbeit mit temporären Projekten können Sie ein Projekt erstellen und damit experimentieren, ohne einen Speicherort angeben zu müssen.

 **Benutzer warnen, wenn der Projekt Speicherort nicht vertrauenswürdig ist** Wenn Sie versuchen, ein neues Projekt zu erstellen oder ein vorhandenes Projekt an einem Speicherort zu öffnen, der nicht vollständig vertrauenswürdig ist (z. b. bei einem UNC-Pfad oder http-Pfad), wird eine Meldung angezeigt. Verwenden Sie diese Option, um anzugeben, ob die Meldung jedes Mal angezeigt wird, wenn Sie versuchen, ein Projekt an einem Speicherort zu erstellen oder zu öffnen, der nicht vollständig vertrauenswürdig ist.

 **Ausgabefenster bei Buildbeginn anzeigen** Zeigt automatisch die Ausgabefenster in der IDE zu Beginn der Projektmappenbuilds an. Weitere Informationen finden Sie unter [How to: Control the Output Window (Vorgehensweise: Steuern des Ausgabefensters)](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Diese Option ist standardmäßig aktiviert.

 **Beim Umbenennen von Dateien zum symbolischen umbenennen auffordern** Wenn diese Option ausgewählt ist, wird ein Meldungs Feld mit der Frage angezeigt, ob [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] auch alle Verweise im Projekt auf das Code Element umbenennen soll.

## <a name="see-also"></a>Siehe auch
 [Dialogfeld „Optionen“, Projekte und Projektmappen, Erstellen und Ausführen](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)

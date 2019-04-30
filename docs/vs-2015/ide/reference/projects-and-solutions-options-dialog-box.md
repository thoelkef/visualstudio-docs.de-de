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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92dac82de96323e1d057991e6570715371c9b272
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438049"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projekte und Projektmappen, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt den Standardpfad der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Projektordner fest und bestimmt das Standardverhalten der Fenster **Ausgabe**, **Aufgabenliste** und **Projektmappen-Explorer** bei der Entwicklung und Erstellung von Projekten. Klicken Sie zum Zugriff auf dieses Dialogfeld auf **Extras/Optionen**, erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.  
  
> [!NOTE]
> Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Diese Hilfeseite wurde unter Berücksichtigung der Option **Allgemeine Entwicklungseinstellungen** verfasst. Klicken Sie im Menü **Tools** auf Einstellungen **Importieren und Exportieren**, um die Einstellungen anzuzeigen oder zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Einstellungen  
 **Speicherort der Projekte**  
 Legt den Standardspeicherort fest, in dem neue Projekte und Projektmappenordner sowie Verzeichnisse erstellt werden. Verschiedene Dialogfelder verwenden auch den in dieser Option festgelegten Speicherort als Ausgangspunkt für Ordner. So verwendet z. B. das Dialogfeld "Projekt öffnen" diesen Speicherort für die Verknüpfung "Meine Projekte".  
  
 **Speicherort von Benutzerprojektvorlagen**  
 Legt den Standardspeicherort fest, der im Dialogfeld **Neues Projekt** verwendet wird, um die Liste **Meine Vorlagen** zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Speicherort von Benutzerelementvorlagen**  
 Legt den Standardspeicherort fest, der im Dialogfeld **Neues Element hinzufügen** verwendet wird, um die Liste **Meine Vorlagen** zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Fehlerliste bei Buildfertigstellung mit Fehlern immer anzeigen**  
 Öffnet das Fenster **Fehlerliste** nachdem der Build fertig gestellt ist nur dann, wenn ein Projekt nicht erstellt werden konnte. Hier werden während des Buildvorgangs aufgetretene Fehler angezeigt. Wenn diese Option deaktiviert ist, treten die Fehler weiterhin auf, aber das Fenster wird nicht geöffnet, wenn der Build abgeschlossen ist. Diese Option ist standardmäßig aktiviert.  
  
 **Aktives Element im Projektmappen-Explorer überwachen**  
 Bei Auswahl dieser Option wird der **Projektmappen-Explorer** automatisch geöffnet, und das aktive Element ist ausgewählt. Das ausgewählte Element ändert sich beim Arbeiten mit unterschiedlichen Dateien in einem Projekt oder einer Projektmappe bzw. mit verschiedenen Komponenten in einem Designer. Wenn diese Option deaktiviert ist, ändert sich die Auswahl im **Projektmappen-Explorer** nicht automatisch. Diese Option ist standardmäßig aktiviert.  
  
 **Erweiterte Buildkonfigurationen anzeigen**  
 Wenn diese Option ausgewählt ist, werden die Optionen für die Buildkonfiguration im Dialogfeld **Projekt-Eigenschaftenseiten** und im Dialogfeld **Projektmappen-Eigenschaftenseiten** angezeigt. Wenn diese Option deaktiviert ist, werden die Optionen für die Buildkonfiguration nicht im Dialogfeld **Projekt-Eigenschaftenseiten** und **Projektmappen-Eigenschaftenseiten** für [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]- und [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Projekte angezeigt, die eine Konfiguration oder beide Konfigurationen (Debug und Release) enthalten. Wenn ein Projekt eine benutzerdefinierte Konfiguration hat, werden die Optionen für die Buildkonfiguration angezeigt.  
  
 Wenn diese Option deaktiviert ist, werden die Befehle im Menü **Erstellen**, z.B. **Projektmappe erstellen**, **Projektmappe neu erstellen** und **Projektmappe bereinigen**, für die Releasekonfiguration ausgeführt, und die Befehle im Menü **Debuggen**, z.B. **Debuggen starten** und **Starten ohne Debugging**, werden für die Debugkonfiguration ausgeführt.  
  
 **Projektmappe immer anzeigen**  
 Bei Auswahl dieser Option werden die Projektmappe und alle Befehle, die für Projektmappen ausgeführt werden, immer in der IDE angezeigt. Wenn diese Option deaktiviert ist, werden alle Projekte als eigenständige Projekte erstellt, und Sie können die Projektmappe im Projektmappen-Explorer oder Befehle, die für Projektmappen ausgeführt werden, in der IDE nicht sehen, wenn die Projektmappe nur ein Projekt enthält.  
  
 **Neue Projekte beim Erstellen speichern**  
 Bei Auswahl dieser Option können Sie einen Speicherort für das Projekt im Dialogfeld **Neues Projekt** festlegen. Wenn diese Option deaktiviert ist, werden alle neuen Projekte als temporäre Projekte erstellt. Bei der Arbeit mit temporären Projekten können Sie ein Projekt erstellen und damit experimentieren, ohne einen Speicherort angeben zu müssen.  
  
 **Benutzer bei nicht vertrauenswürdigem Projektspeicherort warnen**  
 Wenn Sie versuchen, ein neues Projekt zu erstellen oder ein vorhandenes Projekt an einem Speicherort zu öffnen, der nicht vollständig vertrauenswürdig ist (z. B. auf einem UNC-Pfad oder HTTP-Pfad), wird eine Meldung angezeigt. Verwenden Sie diese Option, um anzugeben, ob die Meldung jedes Mal angezeigt wird, wenn Sie versuchen, ein Projekt an einem Speicherort zu erstellen oder zu öffnen, der nicht vollständig vertrauenswürdig ist.  
  
 **Ausgabefenster bei Buildbeginn anzeigen**  
 Zeigt automatisch das Ausgabefenster in der IDE zu Beginn der Projektmappenerstellung an. Weitere Informationen finden Sie unter [Vorgehensweise: Steuern des Ausgabefensters](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Diese Option ist standardmäßig aktiviert.  
  
 **Beim Umbenennen von Dateien zum symbolischen Umbenennen auffordern**  
 Wenn diese Option aktiviert ist, werden Sie in einer Meldung gefragt, ob [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] alle im Projekt enthaltenen Verweise auf das Codeelement umbenennen soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld „Optionen“, Projekte und Projektmappen, Erstellen und Ausführen](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)

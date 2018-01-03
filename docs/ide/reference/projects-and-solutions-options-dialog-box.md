---
title: "Projekte und Projektmappen, Dialogfeld „Optionen“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7b122c66c4fd49cbc8939e5770c56fe8bc48b78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projekte und Projektmappen, Dialogfeld "Optionen"
Legt das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Verhalten im Zusammenhang mit Projekten und Projektmappen fest. Wählen Sie zum Zugriff auf diese Optionen **Extras > Optionen** aus, erweitern Sie **Projekte und Projektmappen**, und klicken Sie auf **Allgemein**.

Die Standardpfade für Projekt- und Vorlagenordner werden über die Registerkarte **Speicherorte** im gleichen Dialogfeld festgelegt.
  
> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Diese Hilfeseite wurde unter Berücksichtigung der Option **Allgemeine Entwicklungseinstellungen** verfasst. Klicken Sie im Menü **Tools** auf Einstellungen **Importieren und Exportieren**, um die Einstellungen anzuzeigen oder zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="general-tab-options"></a>Allgemeine Registerkartenoptionen

**Fehlerliste bei Buildfertigstellung mit Fehlern immer anzeigen**  
Öffnet das Fenster **Fehlerliste** nachdem der Build fertig gestellt ist nur dann, wenn ein Projekt nicht erstellt werden konnte. Hier werden während des Buildvorgangs aufgetretene Fehler angezeigt. Wenn diese Option deaktiviert ist, treten die Fehler weiterhin auf, aber das Fenster wird nicht geöffnet, wenn der Build abgeschlossen ist. Diese Option ist standardmäßig aktiviert.  

**Aktives Element im Projektmappen-Explorer überwachen**  
Bei Auswahl dieser Option wird der **Projektmappen-Explorer** automatisch geöffnet, und das aktive Element ist ausgewählt. Das ausgewählte Element ändert sich beim Arbeiten mit unterschiedlichen Dateien in einem Projekt oder einer Projektmappe bzw. mit verschiedenen Komponenten in einem Designer. Wenn diese Option deaktiviert ist, ändert sich die Auswahl im **Projektmappen-Explorer** nicht automatisch. Diese Option ist standardmäßig aktiviert.  

**Erweiterte Buildkonfigurationen anzeigen**  
Wenn diese Option ausgewählt ist, werden die Optionen für die Buildkonfiguration im Dialogfeld **Projekt-Eigenschaftenseiten** und im Dialogfeld **Projektmappen-Eigenschaftenseiten** angezeigt. Wenn diese Option deaktiviert ist, werden die Optionen für die Buildkonfiguration nicht im Dialogfeld **Projekt-Eigenschaftenseiten** und **Projektmappen-Eigenschaftenseiten** für [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]- und [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]-Projekte angezeigt, die eine Konfiguration oder beide Konfigurationen (Debug und Release) enthalten. Wenn ein Projekt eine benutzerdefinierte Konfiguration hat, werden die Optionen für die Buildkonfiguration angezeigt.  

Wenn diese Option deaktiviert ist, werden die Befehle im Menü **Erstellen**, z.B. **Projektmappe erstellen**, **Projektmappe neu erstellen** und **Projektmappe bereinigen**, für die Releasekonfiguration ausgeführt, und die Befehle im Menü **Debuggen**, z.B. **Debuggen starten** und **Starten ohne Debugging**, werden für die Debugkonfiguration ausgeführt.  

**Projektmappe immer anzeigen**  
Bei Auswahl dieser Option werden die Projektmappe und alle Befehle, die für Projektmappen ausgeführt werden, immer in der IDE angezeigt. Wenn diese Option deaktiviert ist, werden alle Projekte als eigenständige Projekte erstellt, und Sie können die Projektmappe im Projektmappen-Explorer oder Befehle, die für Projektmappen ausgeführt werden, in der IDE nicht sehen, wenn die Projektmappe nur ein Projekt enthält.  

**Neue Projekte beim Erstellen speichern**  
Bei Auswahl dieser Option können Sie einen Speicherort für das Projekt im Dialogfeld **Neues Projekt** festlegen. Wenn diese Option deaktiviert ist, werden alle neuen Projekte als temporäre Projekte erstellt. Bei der Arbeit mit temporären Projekten können Sie ein Projekt erstellen und damit experimentieren, ohne einen Speicherort angeben zu müssen.  

**Benutzer bei nicht vertrauenswürdigem Projektspeicherort warnen**  
Wenn Sie versuchen, ein neues Projekt zu erstellen oder ein vorhandenes Projekt an einem Speicherort zu öffnen, der nicht vollständig vertrauenswürdig ist (z. B. auf einem UNC-Pfad oder HTTP-Pfad), wird eine Meldung angezeigt. Verwenden Sie diese Option, um anzugeben, ob die Meldung jedes Mal angezeigt wird, wenn Sie versuchen, ein Projekt an einem Speicherort zu erstellen oder zu öffnen, der nicht vollständig vertrauenswürdig ist.  

**Ausgabefenster bei Buildbeginn anzeigen**  
Zeigt automatisch das Ausgabefenster in der IDE zu Beginn der Projektmappenerstellung an. Weitere Informationen finden Sie unter [How to: Control the Output Window (Vorgehensweise: Steuern des Ausgabefensters)](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858).

**Beim Umbenennen von Dateien zum symbolischen Umbenennen auffordern**  
Wenn diese Option aktiviert ist, werden Sie in einer Meldung gefragt, ob [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alle im Projekt enthaltenen Verweise auf das Codeelement umbenennen soll.  

**Aufforderung vor der Verschiebung von Dateien zu einem neuen Speicherort**  
Wenn diese Option aktiviert ist, zeigt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ein Bestätigungsmeldungsfeld an, bevor die Speicherorte von Dateien durch Aktionen im Projektmappen-Explorer verändert werden. 

## <a name="locations-tab-options"></a>Optionen der Registerkarte „Speicherorte“

**Speicherort der Projekte**  
Legt den Standardspeicherort fest, in dem von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] neue Projekte und Projektmappenordner erstellt werden. Verschiedene Dialogfelder verwenden auch den in dieser Option festgelegten Speicherort als Ausgangspunkt für Ordner. So verwendet z. B. das Dialogfeld "Projekt öffnen" diesen Speicherort für die Verknüpfung "Meine Projekte".  

**Speicherort von Benutzerprojektvorlagen**  
Gibt den Standardspeicherort an, der vom Dialogfeld **Neues Projekt** verwendet wird, um die Liste **Meine Vorlagen** zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  

**Speicherort von Benutzerelementvorlagen**  
Legt den Standardspeicherort fest, der vom Dialogfeld **Neues Element hinzufügen** verwendet wird, um die Liste **Meine Vorlagen** zu erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../../ide/how-to-locate-and-organize-project-and-item-templates.md). 

## <a name="see-also"></a>Siehe auch  
- [Dialogfeld „Optionen“, Projekte und Projektmappen, Erstellen und Ausführen](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)  
- [Dialogfeld "Optionen", Projekte und Projektmappen, Webprojekte](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
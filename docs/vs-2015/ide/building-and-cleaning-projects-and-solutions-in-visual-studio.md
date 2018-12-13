---
title: Bereinigen von Projekten Lösungen erstellen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05e8d13454ab9698ae855f1e937e85eb287a3a35
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057632"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe der in diesem Thema behandelten Verfahren können Sie alle oder einige Projekte oder Projektelemente in einer Projektmappe erstellen, neu erstellen oder bereinigen. Ein ausführliches Tutorial finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md).

> [!NOTE]
>  In Abhängigkeit der von Ihnen gewählten Einstellungen kann sich die Benutzeroberfläche Ihrer Visual Studio Edition von dem unterscheiden, was in diesem Thema beschrieben wird. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="to-build-rebuild-or-clean-an-entire-solution"></a>So können Sie eine gesamte Projektmappe erstellen, neu erstellen oder bereinigen

1.  Wählen Sie im **Projektmappen-Explorer** die Projektmappe aus, oder öffnen Sie sie.

2.  Wählen Sie dann auf der Menüleiste **Erstellen**, gefolgt von einem der folgenden Befehle aus:

    -   Wählen Sie **Erstellen** oder **Projektmappe erstellen** aus, um nur diejenigen Projektdateien und Komponenten zu kompilieren, die sich seit dem letzten Build geändert haben.

        > [!NOTE]
        >  Der Befehl **Erstellen** wandelt sich in **Projektmappe erstellen**, wenn eine Projektmappe mehr als ein Projekt enthält.

    -   Wählen Sie **Projektmappe neu erstellen** aus, um die Projektmappe zu „bereinigen“ und anschließend alle Projektdateien und Komponenten zu erstellen.

    -   Wählen Sie **Projektmappe bereinigen** aus, um alle eventuellen Interims- und Ausgabedateien zu löschen. Dann bleiben nur die Projekt- und Komponentendateien übrig, und neue Instanzen der Interims- und Ausgabedateien können erstellt werden.

### <a name="to-build-or-rebuild-a-single-project"></a>So erstellen Sie ein einzelnes Projekt oder erstellen es neu

1.  Wählen Sie im **Projektmappen-Explorer** das Projekt aus, oder öffnen Sie es.

2.  Wählen Sie auf der Menüleiste **Erstellen** und dann entweder **Projektname**_erstellen_ oder **Projektname**_neu erstellen_ aus.

    -   Wählen Sie **Projektname**_erstellen_ aus, um nur die Projektkomponenten zu erstellen, die sich seit dem letzten Build geändert haben.

    -   Wählen Sie **Projektname**_neu erstellen_ aus, um das Projekt zu „bereinigen“ und dann die Projektdateien und alle Projektkomponenten zu erstellen.

### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>So erstellen Sie nur das Startprojekt und seine Abhängigkeiten

1. Wählen Sie in der Menüleiste **Extras**, **Optionen**.

2. Klappen Sie im Dialogfeld **Optionen** den Knoten **Projekte und Projektmappen** auf, und wählen Sie dann die Seite **Erstellen und Ausführen** aus.

    Das Dialogfeld **Erstellen und Ausführen, Projekte und Projektmappen, Optionen** wird geöffnet.

3. Aktivieren Sie das Kontrollkästchen **Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**.

    Wenn dieses Kontrollkästchen aktiviert ist, werden nur das aktuelle Startprojekt und seine Abhängigkeiten erstellt, wenn Sie einen der folgenden Schritte ausführen:

   - Wählen Sie in der Menüleiste **Debuggen**, **Starten** (F5) aus.

   - Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen** (STRG+UMSCHALT+B) aus.

     Wenn dieses Kontrollkästchen deaktiviert ist, werden alle Projekte, ihre Abhängigkeiten und die Projektmappendateien erstellt, wenn Sie einen der vorstehenden Befehle ausführen. Dieses Kontrollkästchen ist standardmäßig deaktiviert.

### <a name="to-build-only-the-selected-visual-c-project"></a>So erstellen Sie nur das ausgewählte Visual C++-Projekt

1. Wählen Sie ein [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Projekt aus, und wählen Sie dann in der Menüleiste **Erstellen**, **Nur Projekt** und einen der folgenden Befehle aus:

   - **Nur** *Projektname erstellen*

   - **Nur** *Projektname neu erstellen*

   - **Nur** *Projektname bereinigen*

   - **Nur** *Projektname bereinigen*

     Diese Befehle betreffen nur das ausgewählte [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Projekt, d.h. Projektabhängigkeiten oder Projektmappendateien werden nicht erstellt, neu erstellt, bereinigt oder gelinkt. Abhängig von Ihrer Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] enthält das Untermenü **Nur Projekt** möglicherweise noch weitere Befehle.

### <a name="to-compile-multiple-c-project-items"></a>So kompilieren Sie mehrere C++-Projektelemente

1.  Wählen Sie im **Projektmappen-Explorer** mehrere Dateien aus, die kompilierbare Aktionen aufweisen, öffnen Sie das Kontextmenü für eine dieser Dateien, und wählen Sie dann **Kompilieren** aus.

     Wenn die Dateien Abhängigkeiten aufweisen, werden die Dateien in der Reihenfolge der Abhängigkeit kompiliert. Beim Kompilieren tritt ein Fehler auf, wenn für die Dateien ein vorkompilierter Header erforderlich ist, der zum Zeitpunkt des Kompilierens nicht verfügbar ist. Der Kompiliervorgang verwendet die aktuelle Konfiguration der aktiven Projektmappe.

### <a name="to-stop-a-build"></a>So beenden Sie einen Build

1.  Führen Sie einen der folgenden Schritte aus:

    -   Wählen Sie in der Menüleiste **Erstellen**, **Abbrechen** aus.

    -   Verwenden Sie die Tasten STRG+UNTBR.

## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Anzeigen, speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md) [Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md) [kompilieren und generieren](../ide/compiling-and-building-in-visual-studio.md) [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md) [Debug und Release-Projektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) [Referenz zur C/C++-Erstellung](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md) [Projektmappen und Projekten](../ide/solutions-and-projects-in-visual-studio.md)

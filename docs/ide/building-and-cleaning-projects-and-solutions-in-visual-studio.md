---
title: "Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.BuildProjectPicker"
  - "vs.batchbuild"
helpviewer_keywords: 
  - "Projektmappe bereinigen (Befehl)"
  - "Builds [Visual Studio], Verwalten"
  - "Projektmappenbuildkonfigurationen, Starten"
  - "Projektmappe erstellen (Befehl)"
  - "Projektbuildkonfigurationen, Starten"
  - "Buildkonfigurationen, Starten"
  - "Projektbuildkonfigurationen, Abhängigkeiten"
  - "Projektmappe neu erstellen (Befehl)"
  - "Projektmappenbuildkonfigurationen, Buildreihenfolge"
  - "Builds [Visual Studio], Vorbereiten"
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie den Prozeduren in diesem Thema verwenden, können Sie alle oder einige der Projekte oder der Projektelemente in einer Projektmappe erstellen, neu erstellen oder bereinigen.  Für ein schrittweises Lernprogramm finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md).  
  
> [!NOTE]
>  Die Benutzeroberfläche in der Edition von Visual Studio sich möglicherweise von, was in diesem Thema beschrieben werden, nach den aktiven Einstellungen.  Um die Einstellungen zu ändern, öffnen Sie das Menü **Tools**, und wählen Sie dann **Einstellungen importieren und exportieren** aus.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So können Sie eine komplette Projektmappe erstellen, neu erstellen oder bereinigen  
  
1.  In **Projektmappen\-Explorer** aktivieren oder öffnen Sie die Projektmappe.  
  
2.  Klicken Sie auf der Menüleiste wählen Sie **Build** aus und wählen Sie dann einen der folgenden Befehle:  
  
    -   Wählen Sie **Build** oder **Projektmappe erstellen**, um nur die Projektdateien und Komponenten zu kompilieren, die seit dem letzten Build geändert wurden.  
  
        > [!NOTE]
        >  Der Befehl **Erstellen** wird zu **Projektmappe erstellen**, wenn eine Projektmappe mehrere Projekte umfasst.  
  
    -   Wählen Sie **Projektmappe neu erstellen** "bereinigen" die Projektmappe erstellen und anschließend alle Projektdateien und Komponenten aus.  
  
    -   Wählen Sie **Projektmappe bereinigen**, um alle Zwischen\- und Ausgabedateien zu löschen.  Wenn nur dem Projekt\- und Komponentendateien beizubehalten sind, können neue Instanzen der Zwischen\- und Ausgabedateien erstellt werden.  
  
### So können Sie ein einzelnes Projekt erstellen oder neu erstellen  
  
1.  In **Projektmappen\-Explorer** aktivieren oder öffnen Sie das Projekt.  
  
2.  Klicken Sie auf der Menüleiste wählen Sie **Build** aus und wählen dann entweder **Build***Projektname* oder **Neu erstellen***Projektname* aus.  
  
    -   Wählen Sie **Build***Projektname*, um nur die Projektkomponenten erstellen möchten, die seit dem letzten Build geändert wurden.  
  
    -   Wählen Sie **Neu erstellen***Projektname* "bereinigen" das Projekt und erstellen dann die Projektdateien aus und erstellen.  
  
### So erstellen Sie nur das Startprojekt und dessen Abhängigkeiten  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Tools**, **Optionen** aus.  
  
2.  Im **Optionen** Dialogfeld **Projekte und Projektmappen** erweitern Sie den Knoten, und wählen Sie dann die Seite **Erstellen und Ausführen** aus.  
  
     Das Dialogfeld wird geöffnet. **Erstellen und Ausführen, Projekte und Projektmappen, Optionen**  
  
3.  Wählen Sie das Kontrollkästchen **Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen**.  
  
     Wenn dieses Kontrollkästchen aktiviert wird, wird nur das aktuelle Startprojekt und dessen Abhängigkeiten erstellt werden, wenn Sie einen der folgenden Schritte ausführen:  
  
    -   Klicken Sie auf der Menüleiste wählen Sie **Debuggen**, **Start** aus \(F5\).  
  
    -   Klicken Sie auf der Menüleiste wählen Sie **Build**, **Projektmappe erstellen** Auswahl von \(STRG\+UMSCHALT\+B\).  
  
     Wenn dieses Kontrollkästchen deaktiviert ist, werden alle Projekte, Abhängigkeiten und die Projektmappendateien erstellt, wenn Sie einen der vorangehenden Befehle ausführen.  Dieses Kontrollkästchen ist standardmäßig aktiviert.  
  
### So erstellen Sie nur das ausgewählte Visual C\+\+\-Projekt  
  
1.  Wählen Sie ein Projekt [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], und dann, in der Menüleiste aus, wählen Sie **Build**, **Nur Projekt** und einen der folgenden Befehle:  
  
    -   **Nur erstellen** *Projektname*  
  
    -   **Nur neu erstellen** *Projektname*  
  
    -   **Nur bereinigen** *Projektname*  
  
    -   **Nur verknüpfen** *Projektname*  
  
     Diese Befehle gelten nur für das Projekt [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] zu, das Sie ausgewählt haben, ohne dabei Projektabhängigkeiten oder Lösungsdateien zu erstellen, neu zu erstellen, zu säubern oder zu verknüpfen.  Abhängig von der Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], enthält das Untermenü **Nur Projekt** möglicherweise mehr Befehle.  
  
### So kompilieren Sie mehrere C\+\+\-Projektelemente  
  
1.  In **Projektmappen\-Explorer** wählen Sie mehrere Dateien aus, die kompilierte Aktionen sein, öffnen das Kontextmenü für eine dieser Dateien auswählen und dann **Kompilieren** haben.  
  
     Wenn die Dateien abhängig sind, werden die Dateien in Abhängigkeitsreihenfolge kompiliert.  Der kompilierensvorgang schlägt fehl, wenn die Dateien einen vorkompilierten Header erfordern, der nicht verfügbar ist, wenn Sie kompilieren.  Der kompilierensvorgang wird die aktuelle aktive Projektmappenkonfiguration.  
  
### So beenden Sie einen Build  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf der Menüleiste wählen Sie **Build**, **Abbrechen** aus.  
  
    -   Wählen Sie die STRG\+UNTBR\-Tasten aus.  
  
## Siehe auch  
 [Gewusst wie: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e)   
 [Referenz zur C\/C\+\+\-Erstellung](/visual-cpp/build/reference/c-cpp-building-reference)   
 [Devenv\-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)   
 [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)
---
title: "Konfiguration f&#252;r die Verwaltung der Bereitstellung des Projekts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verwalten der Bereitstellung von Projektkonfigurationen"
  - "Projekte [Visual Studio SDK] Konfiguration für die Verwaltung der Bereitstellung"
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Konfiguration f&#252;r die Verwaltung der Bereitstellung des Projekts
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Bereitstellung ist die Aktion an die Ausgabeelemente einem Buildprozess in den erwarteten Speicherort für das Debuggen und die Installation physisch verschieben.  Beispielsweise kann eine Webanwendung auf einem lokalen Computer erstellt werden und dann auf den Server eingefügt werden.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Möglichkeiten, dass Projekte in der Bereitstellung beteiligt sein können:  
  
-   Als Antragsteller des Bereitstellungsprozesses.  
  
-   Als Manager des Bereitstellungsprozesses.  
  
 Bevor Lösungen bereitgestellt werden können, müssen Sie zuerst ein Bereitstellungsprojekt hinzufügen, Bereitstellungsoptionen zu konfigurieren.  Wenn das Projekt Bereitstellen noch nicht vorhanden ist, werden Sie gefragt, ob Sie diese erstellen möchten, wenn Sie **Projektmappe bereitstellen** vom **Erstellen** Menü oder klicken Sie mit der rechten Maustaste auf die Projektmappe auswählen.  Durch Klicken auf **Ja** öffnet das Dialogfeld **Neues Projekt hinzufügen** mit dem ausgewählten **Remotebereitstellungs\-Assistent** Projekt.  
  
 Der Remotebereitstellungs\-Assistent fordert Sie den Typ der Anwendung \(Windows Internet\) oder Projektausgabegruppen, die aufzunehmenden, alle weiteren Dateien, die Sie einschließen möchten und der Remotecomputer Sie bereitstellen möchten.  Die letzte Seite des Assistenten wird eine Zusammenfassung der ausgewählten Optionen an.  
  
 Projekte, die der Antragsteller eines Bereitstellungsprozess erzeugnisses sind, geben Elemente aus, die auf eine alternative Umgebungen verschoben werden müssen.  Diese Ausgabeelemente werden als Parameter für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>\-Schnittstelle beschrieben, deren Hauptobjekt, wenn Projekte zu ermöglichen, Ausgaben zu gruppieren.  Weitere Informationen hinsichtlich der Implementierung von `IVsProjectCfg2`finden Sie unter [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md).  
  
 Bereitstellungsprojekte, die den Bereitstellungsprozess verwaltet werden, ermöglichen dem Befehl Bereitstellen und reagieren, wenn der Befehl aktiviert ist.  Bereitstellungsprojekte implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>\-Schnittstelle, um die Bereitstellung auszuführen und Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>\-Schnittstelle zu melden Sie Statusereignisse bereit.  
  
 Konfigurationen können Abhängigkeiten angeben, die ihre Build\- oder andere Vorgänge auswirken.  Erstellen oder stellen Sie Abhängigkeiten sind Projekte bereit, die erstellt oder bereitgestellt werden müssen, bevor oder nachdem die Konfigurationen selbst erstellt oder bereitgestellt werden.  Erstellen Sie Abhängigkeiten zwischen Projekten beschrieben werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>\-Schnittstelle bereitstellen und die Abhängigkeiten der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>\-Schnittstelle auf.  Weitere Informationen finden Sie unter [Konfiguration zum Erstellen des Projekts](../../extensibility/internals/project-configuration-for-building.md).  
  
## Siehe auch  
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguration zum Erstellen des Projekts](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguration für die Ausgabe des Projekts](../../extensibility/internals/project-configuration-for-output.md)
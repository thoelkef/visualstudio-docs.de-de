---
title: "Aktualisieren von Projekten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aktualisieren von VSPackages"
  - "Aktualisieren einer Anwendung, Strategien"
  - "VSPackages, Unterstützung der Aktualisierung"
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Aktualisieren von Projekten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Änderungen am Projektmodell von einer Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum nächsten erfordern, dass Projekte und Projektmappen aktualisiert werden, damit sie auf die neuere Version ausgeführt werden können.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] stellt Schnittstellen bereit, die verwendet werden können, um ein Upgrade zu implementieren, die in Projekten verfügen.  
  
## Upgrade\-Strategien  
 Um ein Upgrade zu unterstützen, muss die Implementierung des Projektsystem eine Strategie Upgrade definieren und implementieren.  Wenn Sie die Strategie festlegen, können Sie festlegen, dass parallele Sicherung \(SxS\) Kopien sicherung oder beides zu unterstützen.  
  
-   SxS\-Sicherung bedeutet, dass ein Projekt nur die Dateien kopiert, die an der Stelle aktualisieren und ein geeignetes dem Dateinamen ein, z. B. „.old“ hinzu.  
  
-   Kopiert sicherung bedeutet, dass ein Projekt alle Projektelemente in einem vom Benutzer angegebenen Sicherungsspeicherort kopiert.  Die relevanten Dateien am Speicherort des ursprünglichen Projekts werden dann aktualisiert.  
  
## Wie funktionieren Upgrades  
 Wenn eine Projektmappe, die in einer früheren Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erstellt wurde, in einer neueren Version geöffnet wird, überprüft die IDE die Projektmappendatei, um festzustellen, ob sie aktualisiert werden muss.  Wenn die Aktualisierung erforderlich ist, wird **Upgrade\-Assistent** automatisch gestartet, um den Benutzer durch den Aktualisierungsvorgang zu durchlaufen.  
  
 Wenn eine Projektmappe Aktualisierung erfordert es sich um Abfragen für die einzelnen Projekt factory Strategie Upgrades.  Die Strategie bestimmt, ob das Projekt factory Kopien sicherung oder SxS\-Sicherung unterstützt.  Die Informationen werden an **Upgrade\-Assistent**gesendet, die die Informationen sammelt, die für die Sicherung erforderlich sind und die entsprechenden Optionen für den Benutzer enthält.  
  
### Projektmappen mit mehreren Projekten  
 Wenn eine Lösung mehrere Projekte enthält und das Upgrade strategien voneinander abweichen, z. B. wenn ein C\+\+\-Projekt, das nur SxS\-Sicherung und ein Webprojekt unterstützt, dass unterstützen nur sicherung factorys Projekt kopiert, die über die Upgrade Strategie verhandeln muss.  
  
 Die Projektmappen fragt jede Projekt factory für <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>.  Anschließend wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> , um festzustellen, ob globale Projektdateien Aktualisierung erfordern und die unterstützten Upgrade strategien zu bestimmen.  **Upgrade\-Assistent** wird anschließend aufgerufen.  
  
 Nachdem der Benutzer den Assistenten abgeschlossen wird, wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> um jedem Projekt factory aufgerufen, um die tatsächlichen Upgrade durchzuführen.  Zur Sicherung zu erleichtern, stellen IVsProjectUpgradeViaFactory\-Methoden die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst um die Details des Aktualisierungsvorgangs zu protokollieren.  Dieser Dienst kann nicht zwischengespeichert werden.  
  
 Nachdem alle relevanten globalen Dateien aktualisiert hat, kann jede factory Projekt auswählen, um ein Projekt zu instanziieren.  Die Projektdurchführung muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>unterstützen.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>\-Methode wird anschließend aufgerufen, um alle relevanten Projektelemente zu aktualisieren.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>\-Methode stellt nicht die SVsUpgradeLogger\-Dienstleistung.  Dieser Dienst kann abgerufen werden, indem <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>aufruft.  
  
## Bewährte Methoden  
 Verwenden Sie den <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst, um zu überprüfen, ob Sie eine Datei bearbeiten können, bevor Sie sie bearbeiten und kann diese speichern, bevor Sie sie speichern.  Dies hilft der Sicherung und Implementierungen zu aktualisierenden Bearbeiten von Projektdateien mit Dateien in der Quellcodeverwaltung unzureichender Berechtigungen usw.  
  
 Verwenden Sie den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst während alle Phasen der Sicherung und aktualisieren Sie sie, um Informationen über den Erfolg oder Fehler des Aktualisierungsvorgangs bereitzustellen.  
  
 Weitere Informationen zum Sichern und Aktualisieren von Projekten finden Sie in den Kommentaren in IVsProjectUpgrade für vsshell2.idl.  
  
## Siehe auch  
 [Projekte](../../extensibility/internals/projects.md)   
 [Aktualisieren von benutzerdefinierten Projekten](../../misc/upgrading-custom-projects.md)   
 [Aktualisieren von Projektelementen](../../misc/upgrading-project-items.md)
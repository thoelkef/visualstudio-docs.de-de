---
title: "Aktualisieren von Projektelementen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aktualisieren von Projektelementen"
  - "Projekte [Visual Studio SDK], Elemente aktualisieren"
  - "Projektelemente [Visual Studio], aktualisieren"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Aktualisieren von Projektelementen
Wenn Sie Elemente innerhalb der Projektsysteme hinzufügen oder verwalten, die Sie implementieren, müssen Sie möglicherweise am Projekt aktualisierungsvorgang teilnehmen.  Crystal Reports ist ein Beispiel für ein Element, das dem Projektsystem hinzugefügt werden kann.  
  
 In der Regel möchten Projektelement Implementierungen bereits ein aktualisiertes Projekt und instanziiertes vollständig nutzen, da diese Informationen benötigen, was die Projektverweise sind und welche andere Projekteigenschaften dort befinden, eine Upgrade entscheidung zu treffen.  
  
### Um die Ereignisbenachrichtigung Migrationsupgrade Projekt abrufen  
  
1.  Legen Sie das <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>\-Flag \(definiert in vsshell80.idl\) in der Implementierung des Projektelements fest.  Dadurch wird das Projektelement VSPackage zur automatischen Laden, wenn die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell bestimmt, dass ein Projektsystem bei Aktualisierung ist.  
  
2.  Melden Sie sich die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>\-Schnittstelle zur <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>\-Methode veranschaulicht.  
  
3.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>\-Schnittstelle wird ausgelöst, nachdem die ihre Implementierung Projektsystem Aktualisierungsvorgängen abgeschlossen hat, und das neue aktualisierte Projekt erstellt wird.  Je nach Szenario wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>\-Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>nach dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>oder den <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>\-Methode ausgelöst.  
  
### So aktualisieren Sie die Dateien des Projektelements  
  
1.  Sie müssen den Dateisicherungs Prozess in der Implementierung des Projektelements sorgfältig verwalten.  Dies gilt insbesondere eine parallele Sicherung, in der der `fUpgradeFlag`\-Parameter der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>\-Methode <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>festgelegt wird, in dem Dateien, die gesichert worden wären, in Seiten von Dateien platziert werden, die als „.old“ festgelegt werden.  Die gesicherten Dateien, die älter sind als die Systemzeit, als das Projekt aktualisiert wurde, können festgelegt werden, z. B. veraltet.  Darüber hinaus würden sie überschrieben werden, es sei denn, Sie bestimmte Schritte ausführen, um dies zu verhindern.  
  
2.  Zu dem Zeitpunkt für das Projektelement eine Benachrichtigung der Projekt Migrationsupgrade abruft, wird **Visual Studio\-Konvertierungs\-Assistent** weiterhin angezeigt.  Daher sollten Sie die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>\-Schnittstelle können Sie ein Upgrade von Meldungen an den Assistenten Benutzeroberfläche bereitzustellen.  
  
## Siehe auch  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/de-de/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md)
---
title: Aktualisieren von Projektelementen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project items
- projects [Visual Studio SDK], upgrading items
- project items [Visual Studio], upgrading
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: eb3619e187c7856cf03ee60c8a04cbe527bf0a69
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698683"
---
# <a name="upgrading-project-items"></a>Aktualisieren von Projektelementen
Wenn Sie hinzufügen oder Verwalten von Elementen im Projektsystemen, die Sie nicht implementieren, müssen Sie möglicherweise zur Teilnahme an des Projekt-Upgrade-Prozess. Crystal Reports ist ein Beispiel für ein Element, das an das Projektsystem hinzugefügt werden kann.  
  
 In der Regel Implementierungen der Project-Element einem Projekt bereits vollständig instanziierte und aktualisierten nutzen möchten, weil sie wissen, welches die Projekt-Verweise sind und welche anderen Eigenschaften des Projekts vorhanden sind, um ein Upgrade Entscheidung zu treffen müssen.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Um die Projekt-Upgrade-Benachrichtigung zu erhalten.  
  
1. Legen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> Flag (definiert in der vsshell80.idl) in Ihrer Implementierung der Project-Element. Dies bewirkt, dass Ihr Projektelement VSPackage automatisch geladen, wenn die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shell feststellt, dass ein Projektsystem im Aktualisierungsprozess.  
  
2. Empfehlen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> -Oberfläche über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> Methode.  
  
3. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle wird immer dann ausgelöst, nachdem die systemimplementierung des Projekts ein Upgrade abgeschlossen wurde aus, und die neue, aktualisierte Projekt wird erstellt. Je nach Szenario das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle wird ausgelöst, nachdem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Methoden.  
  
### <a name="to-upgrade-the-project-item-files"></a>So aktualisieren die Element-Projektdateien  
  
1. Sie müssen sorgfältig den Sicherungsvorgang für die Datei in Ihrer Implementierung der Project-Element verwalten. Dies gilt insbesondere für eine Seite-an-Seite-Sicherung, in denen die `fUpgradeFlag` Parameter der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode nastaven NA hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, in Dateien, die gesichert wurden auf der Seite Dateien platziert werden, die als ".old" gekennzeichnet sind. Die gesicherten Dateien, die älter sind als die Systemzeit, wenn das Projekt aktualisiert wurde, können als veraltet festgelegt werden. Darüber hinaus können sie überschrieben werden, es sei denn, Sie bestimmte Schritte, um dies zu verhindern, dass Unternehmen.  
  
2. Zum Zeitpunkt des Projektelements eine Benachrichtigung über das Upgraden von Projekten, ruft der **Visual Studio-Konvertierungs-Assistenten** wird weiterhin angezeigt. Aus diesem Grund sollten Sie die Methoden verwenden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Schnittstelle, um ein Upgrade von Nachrichten auf der Benutzeroberfläche des Assistenten bereitzustellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Konvertierungs-Assistenten](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md)
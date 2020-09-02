---
title: Aktualisieren von Projekt Elementen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698683"
---
# <a name="upgrading-project-items"></a>Aktualisieren von Projektelementen
Wenn Sie Elemente in Projekt Systemen hinzufügen oder verwalten, die Sie nicht implementieren, müssen Sie möglicherweise am Projekt Upgradeprozess teilnehmen. Crystal Reports ist ein Beispiel für ein Element, das dem Projekt System hinzugefügt werden kann.  
  
 In der Regel möchten Projekt Element Implementierungen ein bereits vollständig instanzialisiertes und aktualisiertes Projekt nutzen, da Sie wissen müssen, was die Projekt Verweise sind und welche anderen Projekteigenschaften vorhanden sind, um eine Aktualisierungs Entscheidung zu treffen.  
  
### <a name="to-get-the-project-upgrade-notification"></a>So erhalten Sie die Upgradebenachrichtigung für das Projekt  
  
1. Legen Sie das- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> Flag (definiert in vsshell80. idl) in der Projekt Element Implementierung fest. Dies bewirkt, dass das Projekt Element VSPackage automatisch geladen wird, wenn die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shell ermittelt, dass ein Projekt System gerade aktualisiert wird.  
  
2. Informieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle über die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> Methode.  
  
3. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> -Schnittstelle wird ausgelöst, nachdem die Projekt System Implementierung die Upgradevorgänge abgeschlossen hat und das neue aktualisierte Projekt erstellt wurde. Abhängig vom Szenario wird die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Schnittstelle nach den- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> ,- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> ,-oder- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> Methoden ausgelöst.  
  
### <a name="to-upgrade-the-project-item-files"></a>So aktualisieren Sie die Projekt Element Dateien  
  
1. Sie müssen den Datei Sicherungsprozess in der Projekt Element Implementierung sorgfältig verwalten. Dies gilt insbesondere für eine parallele Sicherung, bei der der- `fUpgradeFlag` Parameter der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode auf festgelegt ist <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> , wobei Dateien, die gesichert wurden, neben Dateien platziert werden, die als ". old" bezeichnet werden. Die gesicherten Dateien, die älter als die Systemzeit waren, als das Projekt aktualisiert wurde, können als veraltet eingestuft werden. Außerdem können Sie überschrieben werden, es sei denn, Sie führen bestimmte Schritte aus, um dies zu verhindern.  
  
2. Wenn das Projekt Element eine Benachrichtigung über das Projekt Upgrade erhält, wird der **Visual Studio-Konvertierungs-Assistent** weiterhin angezeigt. Daher sollten Sie die Methoden der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Schnittstelle verwenden, um upgrademeldungen für die Benutzeroberfläche des Assistenten bereitzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio-Konvertierungs-Assistent](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md)
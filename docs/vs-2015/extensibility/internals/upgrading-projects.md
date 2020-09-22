---
title: Aktualisieren von Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840894"
---
# <a name="upgrading-projects"></a>Aktualisieren von Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Änderungen am Projekt Modell von einer Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in die nächste Version von erfordern möglicherweise, dass Projekte und Projektmappen aktualisiert werden, damit Sie auf der neueren Version ausgeführt werden können. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Stellt Schnittstellen bereit, die zum Implementieren von upgradeunterstützung in ihren eigenen Projekten verwendet werden können.  
  
## <a name="upgrade-strategies"></a>Upgradestrategien  
 Um ein Upgrade zu unterstützen, muss die Implementierung des Projekt Systems eine Upgradestrategie definieren und implementieren. Zum Ermitteln ihrer Strategie können Sie eine parallele (SxS) Sicherung, Kopiesicherung oder beides unterstützen.  
  
- SxS Backup bedeutet, dass in einem Projekt nur die Dateien kopiert werden, für die ein Upgrade durchgeführt werden muss. dabei wird ein geeigneter Dateinamen Suffix hinzugefügt, z. b. ". old".  
  
- Kopiesicherung bedeutet, dass ein Projekt alle Projekt Elemente an einen vom Benutzer bereitgestellten Sicherungs Speicherort kopiert. Die relevanten Dateien am ursprünglichen Projekt Speicherort werden dann aktualisiert.  
  
## <a name="how-upgrade-works"></a>Funktionsweise des Upgrades  
 Wenn eine Projekt Mappe, die in einer früheren Version von erstellt wurde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , in einer neueren Version geöffnet wird, überprüft die IDE die Projektmappendatei, um zu bestimmen, ob Sie aktualisiert werden muss. Wenn ein Upgrade erforderlich ist, wird der **Upgrade-Assistent** automatisch gestartet, um den Benutzer durch den Upgradeprozess zu durchlaufen.  
  
 Wenn eine Projekt Mappe aktualisiert werden muss, fragt Sie jede projektfactory nach ihrer Upgradestrategie ab. Die Strategie bestimmt, ob die projektfactory Kopiesicherung oder SxS-Sicherung unterstützt. Die Informationen werden an den **Upgrade-Assistenten**gesendet, der die für die Sicherung erforderlichen Informationen sammelt und dem Benutzer die entsprechenden Optionen präsentiert.  
  
### <a name="multi-project-solutions"></a>Projektmappen mit mehreren Projekten  
 Wenn eine Projekt Mappe mehrere Projekte enthält und die Upgradestrategien unterschiedlich sind, z. b. Wenn ein C++-Projekt, das nur die SxS-Sicherung unterstützt, und ein Webprojekt, das nur die Kopiesicherung unterstützt, die Projekt-Factorys  
  
 Die Projekt Mappe fragt jede projektfactory nach ab <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Anschließend wird aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> , um zu prüfen, ob globale Projektdateien aktualisiert werden müssen, und um die unterstützten Upgradestrategien zu ermitteln. Anschließend wird der **Upgrade-Assistent** aufgerufen.  
  
 Nachdem der Benutzer den Assistenten abgeschlossen hat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> wird für jede projektfactory aufgerufen, um das tatsächliche Upgrade auszuführen. Um die Sicherung zu vereinfachen, stellen ivsprojectupgradeviafactory-Methoden den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst bereit, um die Details des Upgradevorgangs zu protokollieren. Dieser Dienst kann nicht zwischengespeichert werden.  
  
 Nachdem alle relevanten globalen Dateien aktualisiert wurden, kann jede projektfactory auswählen, ein Projekt zu instanziieren. Die Projekt Implementierung muss unterstützen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird dann aufgerufen, um alle relevanten Projekt Elemente zu aktualisieren.  
  
> [!NOTE]
> Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode stellt keinen SVsUpgradeLogger-Dienst bereit. Dieser Dienst kann durch Aufrufen von abgerufen werden <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Empfehlungen  
 Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Sie den Dienst, um zu prüfen, ob Sie eine Datei bearbeiten können, bevor Sie Sie bearbeiten, und Sie können Sie speichern, bevor Sie gespeichert wird. Dies hilft Ihren Sicherungs-und upgradeimplementierungen bei der Behandlung von Projektdateien in der Quell Code Verwaltung, Dateien mit unzureichenden Berechtigungen usw.  
  
 Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Sie den Dienst in allen Phasen der Sicherung und des Upgrades, um Informationen über den Erfolg oder Misserfolg des Upgradevorgangs bereitzustellen.  
  
 Weitere Informationen zum Sichern und Upgraden von Projekten finden Sie in den Kommentaren für ivsprojectupgrade in vsshell2. idl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kte](../../extensibility/internals/projects.md)   
 [Aktualisieren von benutzerdefinierten Projekten](../../misc/upgrading-custom-projects.md)   
 [Aktualisieren von Projektelementen](../../misc/upgrading-project-items.md)

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
ms.openlocfilehash: 47b4bacb8815db8cf7cb64f47534d1c3b10a8177
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961840"
---
# <a name="upgrading-projects"></a>Aktualisieren von Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Projektmodell wird nun von einer Version von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zur nächsten erfordern, dass Projekte und Projektmappen aktualisiert werden, sodass sie die neuere Version ausgeführt werden können. Die [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] enthält Schnittstellen, die zum Implementieren von Unterstützung in Ihren eigenen Projekten verwendet werden können.  
  
## <a name="upgrade-strategies"></a>Aktualisierungsstrategien  
 Um ein Upgrade zu unterstützen, muss die Project-System-Implementierung definieren und implementieren eine Strategie für die Aktualisierung. Bei der Bestimmung Ihrer Strategie, können Sie auswählen, um Side-by-Side (SxS) Sicherung, Sicherung kopieren oder beides zu unterstützen.  
  
-   Parallele Sicherung bedeutet, dass ein Projekt nur die Dateien kopiert, die ein Upgrade Direktes Hinzufügen einer geeigneten Dateinamensuffix, z. B. ".old".  
  
-   Kopieren Sie die Sicherung bedeutet, dass ein Projekt alle Projektelemente in einen vom Benutzer bereitgestellte Sicherungsspeicherort kopiert. Die relevanten Dateien auf den Speicherort des ursprünglichen Projekts werden anschließend aktualisiert.  
  
## <a name="how-upgrade-works"></a>Funktionsweise von Upgrades  
 Wenn eine Projektmappe, die in einer früheren Version erstellten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird geöffnet, in einer neueren Version, die IDE-Überprüfungen, die die Projektmappendatei, um festzustellen, ob sie ein Upgrade erforderlich ist. Wenn ein Upgrade erforderlich ist, ist die **Aktualisierungs-Assistenten** wird automatisch gestartet, um den Benutzer über den Upgradeprozess geführt.  
  
 Wenn eine Lösung aktualisieren benötigt, wird jedes Projekt-Factory für die Upgrade-Strategie abgefragt. Die Strategie bestimmt, ob die Projektzuordnungsinstanz kopieren oder SxS-Sicherung unterstützt. Die Informationen werden gesendet, um die **Aktualisierungs-Assistenten**, die für die Sicherung erforderliche Informationen erfasst und zeigt die zutreffenden Optionen für dem Benutzer.  
  
### <a name="multi-project-solutions"></a>Projektmappen mit mehreren Projekten  
 Wenn eine Projektmappe mehrere Projekte enthält, und die Aktualisierungsstrategien unterscheiden, wie z. B. beim Erstellen eines C++-Projekts, das nur parallele Sicherung unterstützt und ein Webprojekt, die nur Sicherung kopieren unterstützt, die projektfactorys der Aktualisierungsstrategie aushandeln müssen.  
  
 Die Lösung Abfragen für jedes Projekt-Factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Es ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> um festzustellen, ob die globale Projektdateien benötigen aktualisieren und die unterstützten Aktualisierungsstrategien zu ermitteln. Die **Aktualisierungs-Assistenten** wird dann aufgerufen.  
  
 Nach Abschluss des Assistenten, durch der Benutzer <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> für jedes Projekt-Factory zum Ausführen des tatsächlichen Upgrades aufgerufen wird. Um die Sicherung zu erleichtern, IVsProjectUpgradeViaFactory dienen der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> Dienst, der die Details des Upgradeprozesses protokollieren. Dieser Dienst kann nicht zwischengespeichert werden.  
  
 Nach der Aktualisierung aller relevanten globale Dateien kann jedes Projekt-Factory zum Instanziieren ein Projekt auswählen. Die Projekt-Implementierung unterstützen muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Methode wird aufgerufen, um alle relevanten Projektelemente zu aktualisieren.  
  
> [!NOTE]
>  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Methode der SVsUpgradeLogger-Dienst nicht bereitstellt. Dieser Dienst abgerufen werden kann, durch den Aufruf <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst zu überprüfen, ob Sie eine Datei vor der Bearbeitung bearbeiten können, und vor dem Speichern speichern können. Dadurch wird die Sicherung und Upgrade Implementierungen verarbeiten, Projektdateien unter quellcodeverwaltung, Dateien mit nicht genügend Berechtigungen, und So weiter.  
  
 Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> service in allen Phasen der Sicherung und upgrade, um Informationen zu den Erfolg oder Misserfolg des Upgradevorgangs bereitzustellen.  
  
 Weitere Informationen zum Sichern und Aktualisieren von Projekten finden Sie unter die Kommentare für IVsProjectUpgrade in vsshell2.idl.  
  
## <a name="see-also"></a>Siehe auch  
 [Projekte](../../extensibility/internals/projects.md)   
 [Aktualisieren von benutzerdefinierten Projekten](../../misc/upgrading-custom-projects.md)   
 [Aktualisieren von Projektelementen](../../misc/upgrading-project-items.md)

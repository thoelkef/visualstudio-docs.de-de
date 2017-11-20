---
title: "Benutzerdefinierte Oberfläche (Source Control VSPackage) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6138ffcd0c56b87e9e29a316aa2ae0ad9f982e18
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="custom-user-interface-source-control-vspackage"></a>Benutzerdefinierte Oberfläche (Source Control VSPackage)
Eine VSPackage deklariert die Menüelemente und deren Standardstatus über die Visual Studio-Befehlstabelle (VSCT)-Datei. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE) werden die Menüelemente in ihrem Standard angezeigt, bis das VSPackage geladen wurde. Anschließend kann die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode wird aufgerufen, um zu aktivieren oder Deaktivieren von Menüelementen.  
  
 Eine VSPackage kann einen Registrierungsschlüssel festlegen, damit das VSPackage automatisch geladen werden kann, können Sie je nach einem Befehl Benutzerkontext-Benutzeroberfläche (UI), obwohl eine Quelle zu steuern, in der Regel sollte VSPackage statt nur Wechsel zu einem bestimmten UI-Kontext Bedarfsgesteuert laden. Weitere Informationen zum Registrierungsschlüssel AutoLoadPackages finden Sie unter [Verwalten von VSPackages](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>VSPackage-Benutzeroberfläche  
 Eine Source Control-Paket wird als ein VSPackage implementiert und verwendet keinen Benutzeroberflächen aus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jede quellcodeverwaltung VSPackage muss eigene Benutzeroberflächenelemente, z. B. Menüelemente, Menügruppen Toolfenster, Symbolleisten und Benutzeroberflächenelemente erforderlich zum Festlegen von Optionen quellcodeverwaltung des VSPackage bestimmte angeben. Diese Elemente der Benutzeroberfläche können statisch oder dynamisch aktiviert werden. Statische Elemente der Benutzeroberfläche in einer VSCT-Datei definiert sind und angezeigt werden, ob das VSPackage oder nicht geladen wird. Dynamische Elemente der Benutzeroberfläche möglicherweise sichtbar je nach einem bestimmten Befehl UI-Kontext, z. B. <xref:EnvDTE.Constants.vsContextNoSolution>, oder als Ergebnis eines Aufrufs an die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Die Sichtbarkeit der dynamischen Elemente der Benutzeroberfläche entspricht der Strategie für das verzögerte Laden von VSPackages.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>UI-Beschränkungen Source Control VSPackages  
 Da das Quellsteuerelement VSPackage nicht aus der IDE entfernt werden kann, nachdem es geladen wird, muss das VSPackage einen inaktiven Status eingeben können. Wenn eine VSPackage Benachrichtigung erhält, dass es nicht mehr aktiv ist, wird das VSPackage die Benutzeroberfläche deaktiviert und ignoriert externe IDE ein Eingreifen. Die VSPackage Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode sollten Befehle ausblenden, wenn das VSPackage nicht aktiv ist.  
  
 Alle Datenquellen-Steuerelements, das VSPackage implementieren muss die `IVsSccProvider` Schnittstelle. Zwei Methoden der Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, von dem VSPackage implementiert werden muss.  
  
 Die Datenquellen-Steuerelements, das VSPackage möglicherweise verschiedene IDE-Ereignisse, die von implementiert werden abonniert haben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>und so weiter. Darüber hinaus das VSPackage möglicherweise haben implementiert Registrierung aktiviert eine Rückrufschnittstelle, wie z. B. die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Dazu müssen alle inaktiven Zustand ignoriert werden.  
  
 Die folgende Liste enthält die Schnittstellen, die von den aktiven Status des VSPackage ein Datenquellen-Steuerelements betroffen sind:  
  
-   Project-Dokumente Ereignisse zu verfolgen.  
  
-   Projektmappenereignisse, die.  
  
-   Lösung Persistenz-Schnittstellen. Wenn inaktiv ist, sollten Pakete nicht auf .sln und .suo-Dateien geschrieben.  
  
-   Eigenschaftenextender.  
  
 Die erforderliche <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, und auch optionalen Schnittstellen zugeordneten Datenquellen-Steuerelements werden nicht aufgerufen, wenn das Quellsteuerelement VSPackage inaktiv ist.  
  
 Wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE gestartet wird, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des Kontexts Befehl UI auf die ID der Standardeinstellung Quellcodeverwaltungs VSPackage-ID. Dies bewirkt, dass die statische Benutzeroberfläche des aktiven Datenquellen-Steuerelements VSPackage in der IDE angezeigt werden, ohne tatsächlich laden das VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]für das VSPackage zu registrierenden hält [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> vor dem alle Aufrufe an das VSPackage.  
  
 Die folgende Tabelle beschreibt spezifische Details darüber, wie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Blendet Sie aus verschiedenen UI-Elemente.  
  
|Benutzeroberflächenautomatisierungs-Element|Beschreibung|  
|-------------|-----------------|  
|Menüs und Symbolleisten|Das Quellcodeverwaltungspaket muss die Menü- und Symbolleistenelemente Sichtbarkeit Anfangszustände festgelegt, auf die Datenquellen-Steuerelement Paket-ID in der [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) Abschnitt der VSCT-Datei. Dies ermöglicht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE zum Festlegen des Status der Menüelemente entsprechend ohne laden das VSPackage und eine Implementierung von Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode.|  
|Toolfenster|Die Datenquellen-Steuerelements VSPackage Blendet alle Toolfenster, die er besitzt, wenn sie inaktive bereitgestellt wird.|  
|Datenquellen-Steuerelements VSPackage-spezifischen Optionen-Seiten|Der Registrierungsschlüssel HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts kann eine VSPackage die Kontexte festgelegt, in denen dafür seine Optionsseiten angezeigt werden. Ein Registrierungseintrag unter diesem Schlüssel mithilfe von Dienst-ID (SID) des der quellcodeverwaltungsdienst und einen DWORD-Wert von 1 Vorlagenkörpers erstellt werden müssten. Eintreten ein UI-Ereignis in einem Kontext die Datenquellen-Steuerelements, das VSPackage registriert ist, wird das VSPackage aufgerufen werden, wenn er aktiv ist.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
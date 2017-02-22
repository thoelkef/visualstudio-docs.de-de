---
title: "Benutzerdefinierte Oberfl&#228;che (Source Control VSPackage) | Microsoft Docs"
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
  - "Benutzeroberfläche, Source Control-Pakete"
  - "Quellcode-Verwaltungspaketen-Benutzeroberfläche"
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Benutzerdefinierte Oberfl&#228;che (Source Control VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage deklariert seine Menüelemente und ihre Standardannahhmen von der Datei Studio\-Befehls\-Tabelle \(Visual .vsct\).  Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) werden die Menüelemente im Standardannahhmen an, bis VSPackages geladen wurde.  Anschließend wird die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>\-Methode aufgerufen, um die Menüelemente zu aktivieren oder zu deaktivieren.  
  
 VSPackage kann einen Registrierungsschlüssel festlegen, sodass ein VSPackage Befehl je nach einem Kontext der Benutzeroberfläche \(UI\) automatisch geladen werden, obwohl in der Regel eine Quellcodeverwaltung VSPackage bei Bedarf laden soll, statt an einen Kontext der bestimmten Benutzeroberfläche nur zu wechseln.  Weitere Informationen zu den AutoLoadPackages\-Registrierungsschlüssel finden Sie unter [Verwalten von VSPackages](../../extensibility/managing-vspackages.md).  
  
## VSPackage Benutzeroberfläche  
 Ein Paket wird als Quellcodeverwaltung ein VSPackage implementieren und keine Benutzeroberfläche von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet.  Jede Quellcodeverwaltung VSPackage muss seine eigene Benutzeroberflächenelemente wie Menü Menüelemente Gruppen, Toolfenster, Symbolleisten und jedes erforderliche Benutzeroberfläche zum Festlegen von Optionen angeben, die der Quellcodeverwaltung VSPackage spezifisch sind.  Diese Benutzeroberflächenelemente können statisch oder dynamisch aktiviert sind.  Statische Benutzeroberflächenelemente werden in einer .vsct\-Datei definiert und werden angezeigt, ob ein VSPackage oder nicht geladen wird.  Dynamische Benutzeroberflächenelemente sind davon abhängig von einem bestimmten Kontext Befehlsbenutzeroberflächen, z. B. <xref:EnvDTE.Constants.vsContextNoSolution>oder als Ergebnis eines Aufrufs der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>\-Methode sichtbar.  Die Sichtbarkeit von dynamischen Benutzeroberflächenelementen stimmt mit der Strategie für das verzögerte Laden von VSPackages.  
  
## VSPackages auf Quellcodeverwaltung Benutzeroberfläche\-Einschränkungen  
 Da die Quellcodeverwaltung ein VSPackage über die IDE nicht entfernt werden können, nachdem sie geladen wurde, muss ein VSPackage in der Lage sein, einen inaktiven Zustand übergegangen ist.  Wenn ein VSPackage Benachrichtigung erhält, dass sie nicht mehr aktiv ist, VSPackages deaktiviert sein Benutzeroberfläche und ignoriert jede externe IDE\-Interaktion.  Die VSPackages Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>\-Methode sollte Befehle ausgeblendet, wenn ein VSPackage nicht aktiv ist.  
  
 Jede Quellcodeverwaltung VSPackage muss die `IVsSccProvider`\-Schnittstelle implementieren.  Zwei Methoden der Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, müssen von VSPackages implementiert werden.  
  
 Die Quellcodeverwaltung VSPackage abonniert möglicherweise zu unterschiedlichen IDE\-Ereignissen, die von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>implementiert werden, usw.  Außerdem kann ein VSPackage Rückruf Registrierung\-aktivierte Schnittstellen implementiert, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>.  Diese müssen alle ignoriert werden, wenn inaktiv.  
  
 In der folgenden Liste sind die Schnittstellen aufgeführt, die in den aktiven Zustand einer Quellcodeverwaltung VSPackage betroffen sind:  
  
-   Titel\-Projektdokumentations Events.  
  
-   Projektmappen Events.  
  
-   Dauerhaftigkeit von Projektmappen Schnittstellen.  Wenn keine Pakete sollten inaktiv, .suo\-Dateien SLN\- und zu schreiben.  
  
-   Eigenschaftextender.  
  
 Erforderliche <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>und auch keine optionalen Schnittstellen, die Quellcodeverwaltung verknüpft sind, werden nicht aufgerufen, wenn die Quellcodeverwaltung VSPackages deaktiviert ist.  
  
 Wenn die IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] beginnt, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Kontext Befehlsbenutzeroberflächen auf die ID der aktuellen Standardeinstellung quellcodeverwaltung VSPackages festlegt.  Dies bewirkt, dass das statische Benutzeroberfläche der aktiven Quellcodeverwaltung VSPackage, in der IDE angezeigt werden, ohne tatsächlich VSPackages geladen werden soll.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Pausen, damit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit einem VSPackage über <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> registriert, bevor ein VSPackage alle Aufrufe vornimmt.  
  
 In der folgenden Tabelle werden bestimmte Details darüber, wie sich das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE andere Benutzeroberflächenelemente ausblendet.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|Menüs und Symbolleisten|Das Paket muss die ursprünglichen Quellcodeverwaltung Menü\- und Symbolleisten sichtbarkeits Bedingungen zur Quellcodeverwaltung paket\-id im [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)\-Abschnitt der .vsct\-Datei festlegen.  Dies ermöglicht das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, um den Zustand der Menüelemente entsprechend festzulegen, ohne VSPackages geladen und eine Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>\-Methode aufzurufen.|  
|Toolfenster|Die Quellcodeverwaltung VSPackage blendet alle Toolfenster aus, die dieser besitzt, wenn sie deaktiviert.|  
|Quellcodeverwaltung VSPackage\-Besondere Optionsseiten|Der Registrierungsschlüssel HKLM \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ X.Y \\ ToolsOptionsPages \\ VisibilityCmdUIContexts VSPackage können die Kontexte festlegen, in denen es erforderlich ist, seine Optionsseiten angezeigt werden soll.  Ein Registrierungseintrag unter diesem Schlüssel erstellt werden kann, muss der Dienst ID \(SID\) des verwendeten diensts Quellcodeverwaltung und ihr einen DWORD\-Wert 1. zuwies.  Sobald ein Benutzeroberfläche\-Ereignis in einem Kontext auftritt, wird die Quellcodeverwaltung bezeichnet wird, mit einem VSPackage VSPackages registriert, wenn es aktiv ist.|  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution>   
 [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
---
title: Benutzerdefinierte Benutzeroberfläche (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09ab1bb7e44ee2772023a73632ca194796bbb33e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631886"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Benutzerdefinierte Benutzeroberfläche (Datenquellen-Steuerelement-VSPackage)
Eine VSPackage deklariert seine Menüelemente und deren Standardstatus über die Visual Studio-Befehlstabelle (*VSCT*) Datei. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) werden die Menüelemente im Standardzustand angezeigt, bis das VSPackage geladen wird. Anschließend kann die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufgerufen, um aktivieren oder Deaktivieren von Menüelementen.

 Eine VSPackage kann einen Registrierungsschlüssel festlegen, damit das VSPackage je nach Kontext Benutzeroberfläche (UI) Befehl automatisch geladen werden kann, obwohl in der Regel von Quellcode VSPackage sollte geladen bei Bedarf statt nur Wechsel zu einem bestimmten UI-Kontext. Weitere Informationen zu den **AutoLoadPackages** Registrierung, finden Sie unter [verwalten VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>VSPackage-Benutzeroberfläche
 Ein Quellcodeverwaltungspaket wird als ein VSPackage implementiert und verwendet keine Benutzeroberflächenelemente von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jede quellcodeverwaltung VSPackage muss eine eigene UI-Elemente wie z. B. Menüelemente, Menügruppen, Toolfenster, Symbolleisten und erforderliche Benutzeroberflächenelemente zum Festlegen von Optionen auf das Quellcodeverwaltungs-VSPackage bestimmte angeben. Diese Elemente der Benutzeroberfläche können statisch oder dynamisch aktiviert werden. Statische Elemente der Benutzeroberfläche werden definiert, einem *VSCT* Datei, und werden angezeigt, ob das VSPackage, oder nicht geladen wird. Dynamische Elemente der Benutzeroberfläche möglicherweise sichtbar je nach einer bestimmten befehlsbenutzeroberflächenkontext, z. B. <xref:EnvDTE.Constants.vsContextNoSolution>, oder als Ergebnis eines Aufrufs der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. Die Sichtbarkeit der dynamischen Elemente der Benutzeroberfläche ist mit der Strategie für das verzögerte Laden von VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>UI-Einschränkungen für die quellcodeverwaltung VSPackages
 Da das Quellcodeverwaltungs-VSPackage nicht aus der IDE entfernt werden kann, nachdem sie geladen wurden, muss das VSPackage einen inaktiven Status eingeben können. Wenn eine VSPackage die Benachrichtigung empfängt, dass es nicht mehr aktiv ist, wird das VSPackage deaktiviert die Benutzeroberfläche und ignoriert alle externen IDE-Interaktion. Die VSPackage Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode sollten Befehle ausblenden, wenn das VSPackage nicht aktiv ist.

 Alle Datenquellen-Steuerelement, das VSPackage implementiert werden muss die `IVsSccProvider` Schnittstelle. Zwei Methoden für die Schnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, muss vom VSPackage implementiert werden.

 Das Datenquellen-Steuerelement, das VSPackage möglicherweise verschiedene IDE-Ereignisse, die von implementiert werden abonniert haben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>und so weiter. Darüber hinaus das VSPackage kann haben implementiert Registrierung-fähigen Rückrufschnittstellen, wie z. B. die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>. Diese Schnittstellen müssen alle inaktiven Zustand ignoriert werden.

 Die folgende Liste enthält die Schnittstellen, die von den aktiven Zustand eines Quellcodeverwaltungs-VSPackage betroffen sind:

- Nachverfolgen von projektdokumentereignissen.

- Projektmappen-Ereignissen.

- Lösung Persistenz-Schnittstellen. Wenn inaktiv, Pakete sollten nicht geschrieben werden *sln* und *suo* Dateien.

- Eigenschaftenextender.

  Die erforderlichen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, und auch alle optionalen Schnittstellen, die Datenquellen-Steuerelement zugeordnet werden nicht aufgerufen, wenn das Quellcodeverwaltungs-VSPackage aktiv ist.

  Wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE gestartet wird, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird von der befehlsbenutzeroberflächenkontext auf die ID des standardmäßigen Quellcodeverwaltungs-VSPackage-ID. Dies bewirkt, dass die statische Benutzeroberfläche, der das aktive Quellcodeverwaltungs-VSPackage in der IDE angezeigt werden, ohne Sie zu das VSPackage laden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hält für das VSPackage, um beim Registrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> bevor er alle Aufrufe für das VSPackage ausführt.

  Die folgende Tabelle beschreibt spezifische Details zur Funktionsweise des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Blendet Sie aus verschiedenen UI-Elemente.

| UI-Element | Beschreibung |
| - | - |
| Menüs und Symbolleisten | Das Quellcodeverwaltungspaket muss die Menü- und Symbolleistenobjekte Sichtbarkeit Anfangszustände festgelegt, auf die Steuerelement-Paket-ID in der [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) Teil der *VSCT* Datei. Dies ermöglicht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, um den Status der Menüelemente ordnungsgemäß festgelegt werden, ohne das VSPackage zu laden und eine Implementierung von der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode. |
| Toolfenster | Das Quellcodeverwaltungs-VSPackage Blendet alle Toolfenster, die er besitzt, wenn es inaktiv geschaltet wird. |
| Quellcodeverwaltung VSPackage-spezifische Optionen-Seiten | Der Registrierungsschlüssel **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** ermöglicht eine VSPackage legen Sie die Kontexte, in der sie seine Optionsseiten anzuzeigende erfordert. Ein Registrierungseintrag unter diesem Schlüssel müsste erstellt werden, indem Sie die Dienst-ID (SID) von den quellcodeverwaltungsdienst verwenden und zuweisen einen DWORD-Wert von 1. Ein Benutzeroberflächen-Ereignis in einem Kontext das Datenquellen-Steuerelement auftreten, die VSPackage registriert ist, wird das VSPackage aufgerufen, wenn er aktiv ist. |

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)
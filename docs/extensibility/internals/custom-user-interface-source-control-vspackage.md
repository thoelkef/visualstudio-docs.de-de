---
title: Benutzerdefinierte Benutzeroberfläche (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708929"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Benutzerdefinierte Benutzeroberfläche (Quellcodeverwaltung VSPackage)
Ein VSPackage deklariert seine Menüelemente und ihre Standardzustände über die Visual Studio-Befehlstabelle (*.vsct*) Datei. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) zeigt die Menüelemente in ihrem Standardzuserat an, bis das VSPackage geladen wird. Anschließend wird <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> die Methode aufgerufen, um Menüelemente zu aktivieren oder zu deaktivieren.

 Ein VSPackage kann einen Registrierungsschlüssel festlegen, sodass das VSPackage in Abhängigkeit von einem Benutzerbenutzeroberflächenkontext automatisch geladen werden kann, obwohl in der Regel ein Quellcodeverwaltungs-VSPackage bei Bedarf geladen werden sollte, anstatt nur zu einem bestimmten UI-Kontext zu wechseln. Weitere Informationen zum **AutoLoadPackages-Registrierungsschlüssel** finden Sie unter Verwalten von [VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>VSPackage-Benutzeroberfläche
 Ein Quellcodeverwaltungspaket wird als VSPackage implementiert und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet keine Benutzeroberfläche von . Jedes Quellcodeverwaltungs-VSPackage muss seine eigenen UI-Elemente wie Menüelemente, Menügruppen, Toolfenster, Symbolleisten und alle erforderlichen Benutzeroberflächen für Einstellungsoptionen angeben, die für das Quellcodeverwaltungs-VSPackage spezifisch sind. Diese UI-Elemente können statisch oder dynamisch aktiviert werden. Statische UI-Elemente werden in einer *.vsct-Datei* definiert und unabhängig davon angezeigt, ob das VSPackage geladen ist oder nicht. Dynamische UI-Elemente können abhängig von einem bestimmten <xref:EnvDTE.Constants.vsContextNoSolution>Befehlsbenutzerkontext, z. B. , oder als Ergebnis eines Aufrufs der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode sichtbar sein. Die Sichtbarkeit dynamischer UI-Elemente entspricht der Strategie für das verzögerte Laden von VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>UI-Einschränkungen für die Quellcodeverwaltung VSPackages
 Da das Quellcodeverwaltungs-VSPackage nach dem Laden nicht aus der IDE entfernt werden kann, muss das VSPackage in einen inaktiven Zustand gelangen können. Wenn ein VSPackage eine Benachrichtigung erhält, dass es nicht mehr aktiv ist, deaktiviert das VSPackage seine Benutzeroberfläche und ignoriert jede externe IDE-Interaktion. Die VSPackage-Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode sollte Befehle ausblenden, wenn das VSPackage nicht aktiv ist.

 Jede Quellcodeverwaltung VSPackage `IVsSccProvider` muss die Schnittstelle implementieren. Zwei Methoden auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>Schnittstelle und , müssen vom VSPackage implementiert werden.

 Die Quellcodeverwaltung VSPackage hat möglicherweise verschiedene IDE-Ereignisse abonniert, die von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>, usw. implementiert werden. Außerdem hat das VSPackage möglicherweise registrierungsfähige Rückrufschnittstellen implementiert, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>z. B. die . Diese Schnittstellen müssen alle ignoriert werden, wenn sie inaktiv sind.

 Die folgende Liste zeigt die Schnittstellen, die vom aktiven Status eines Quellcodeverwaltungs-VSPackage betroffen sind:

- Verfolgen Sie Projektdokumente Ereignisse.

- Lösungsereignisse.

- Lösungspersistenzschnittstellen. Wenn sie inaktiv sind, sollten Pakete nicht in *.sln-* und *.suo-Dateien* schreiben.

- Eigenschaftenverlängerer.

  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> erforderlichen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>und , sowie alle optionalen Schnittstellen, die mit der Quellcodeverwaltung verknüpft sind, werden nicht aufgerufen, wenn die Quellcodeverwaltung VSPackage inaktiv ist.

  Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestartet wird, wird der Kontext der Befehlsbenutzeroberfläche auf die ID der aktuellen Standard-Quellcodeverwaltung VSPackage ID festgelegt. Dadurch wird die statische Benutzeroberfläche des aktiven Quellcodesteuerelements VSPackage in der IDE angezeigt, ohne das VSPackage tatsächlich zu laden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hält an, dass sich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] das <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage über das registriert, bevor es Aufrufe des VSPackage abgibt.

  In der folgenden Tabelle werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spezifische Details dazu beschrieben, wie die IDE verschiedene UI-Elemente ausblendet.

| UI-Element | BESCHREIBUNG |
| - | - |
| Menüs und Symbolleisten | Das Quellcodeverwaltungspaket muss den anfänglichen Menü- und Symbolleistensichtbarkeitszu-Bereich auf die Quellcodeverwaltungspaket-ID im Abschnitt [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) der *.vsct-Datei* festlegen. Dadurch kann [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die IDE den Status der Menüelemente entsprechend festlegen, ohne das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage zu laden und eine Implementierung der Methode aufzurufen. |
| Toolfenster | Das Quellcodeverwaltungs-VSPackage blendet alle Toolfenster aus, die es besitzt, wenn es inaktiv gemacht wird. |
| Quellcodeverwaltung VSPackage-spezifische Optionsseiten | Mit dem Registrierungsschlüssel **HKLM-SOFTWARE-Microsoft-VisualStudio-X.Y-ToolsOptionsPages-VisibilityCmdUIContexts** kann ein VSPackage die Kontexte festlegen, in denen seine Optionsseiten angezeigt werden müssen. Ein Registrierungseintrag unter diesem Schlüssel müsste mithilfe der Dienst-ID (SID) des Quellcodeverwaltungsdienstes erstellt und ihm den DWORD-Wert 1 zugewiesen werden. Wenn ein UI-Ereignis in einem Kontext auftritt, in dem das Quellcodeverwaltungspaket VSPackage registriert ist, wird das VSPackage aufgerufen, wenn es aktiv ist. |

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)

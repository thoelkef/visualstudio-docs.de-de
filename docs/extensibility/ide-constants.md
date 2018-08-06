---
title: IDE-Konstanten | Microsoft-Dokumentation
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23512005bed66550b4a1de0f0a2de830d9fb823b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498992"
---
# <a name="ide-constants"></a>IDE-Konstanten

Die <xref:Microsoft.VisualStudio.VSConstants> Klasse enthält die Konstanten, die die integrierte Entwicklungsumgebung (IDE) spezifisch sind und, die zuvor nur in Headerdateien definiert wurden.

## <a name="logical-and-physical-views"></a>Logische und physische Ansichten

|Wert|Beschreibung|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler sollten diesen Wert zum Übergeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall auf möglichen Codeansichten.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall gefüllt mit möglichen <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> Debug-Ansichten, die zur gleichen Ansicht wie ordnen <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall um **Formular anzeigen** -Designer-Ansichten.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall die standardmäßige/primäre Ansicht der Editorfactory.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall für ein Dokument oder -Text-Editor-Ansicht.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, die den Benutzer auffordert, welche benutzerdefinierte Ansicht verwendet.|

## <a name="editor-factory-flags"></a>Editor-Factory-Flags

|Wert|Beschreibung|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Ein veraltetes Flag bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode.|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, Methode, dies weist darauf hin Editorfactory sollte die notwendigen Korrekturen durchführen.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> -Methode, dieses Flag schließen sich gegenseitig aus der [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> -Methode, dies gibt die Editorfactory sollte den Editor erstellen, ohne eine Benutzeroberfläche (UI) anzuzeigen.|

## <a name="visual-studio-errors"></a>Visual Studio-Fehler

|Wert|Beschreibung|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Eine Konstante, die von Schnittstellen zurückgegeben werden, um asynchrones Verhalten bei der das Objekt bereits ausgelastet ist|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für "nicht kompatible Dokumentendaten".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und angibt "Paket nicht geladen."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und angibt, die den "Projekt bereits vorhanden."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und, der angibt, "Projektkonfiguration fehlgeschlagen".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und angibt "Projekt nicht geladen."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und, der angibt, "Projektmappe bereits geöffnet."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und, der angibt, "Projektmappe nicht geöffnet."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Die von der buildschnittstellen, die Parameter zum Angeben eines Arrays von haben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> -Schnittstelle, aber die Implementierung der Methode nur auf alle Ausgaben anwenden kann.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode gibt diesen Wert zurück, wenn das Dokument ein Format hat, die im Editor nicht geöffnet werden kann.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Ein HRESULT-Wert, der angibt, dass der Benutzer die Schaltfläche "zurück" in erreicht eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Assistenten.|

## <a name="visual-studio-constants"></a>Visual Studio-Konstanten

|Wert|Beschreibung|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Fehler HRESULT, das für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und angibt "Projekt weitergeleitet".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Eine Konstante, die für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für einen "toolboxmarker".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Eine Konstante, die für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für die Übertragung einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die den Anfang der Modalität angibt.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Eine Konstante, die für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für die Übertragung einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die das Ende der Modalität angibt.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Eine Konstante, die für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für die Übertragung einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die angibt, dass sich die befehlsleistenmetrik geändert haben.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Eine Konstante, die für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , der angibt, dass ein Cookie nicht festgelegt wurde.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Elementbezeichner, der das Fehlen eines Projektelements darstellt. Dieser Wert wird verwendet, wenn keine aktuelle Auswahl vorhanden ist.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Elementbezeichner, der den Stamm einer Projekthierarchie darstellt und wird verwendet, um die gesamte Hierarchie, im Gegensatz zu einem einzelnen Element zu identifizieren.|
|[VSITEMID. Auswahl](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Elementbezeichner, der darstellt, die aktuell ausgewählte Element oder Elemente, die den Stamm der Hierarchie enthalten können.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Beschreibt, welche Komponente der IDE einfach, im ausgewählt wurde ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> aufrufen, z. B.

|Konstante|Wert|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0 x 4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0 x 5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Konstanten verwendet, um einen neuen Auswahlzustand anzugeben.

|Konstante|Wert|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Konstanten der Komponente Selector-Dialogfeld

|Konstante|Wert|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Siehe auch

- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
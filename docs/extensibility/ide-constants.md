---
title: IDE-Konstanten | Microsoft Docs
ms.date: 03/22/2018
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710504"
---
# <a name="ide-constants"></a>IDE-Konstanten

Die <xref:Microsoft.VisualStudio.VSConstants> Klasse stellt Konstanten bereit, die für die integrierte Entwicklungsumgebung (IDE) spezifisch sind und zuvor nur in Headerdateien definiert wurden.

## <a name="logical-and-physical-views"></a>Logische und physische Ansichten

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` Handler sollten diesen Wert <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> an die Methode übergeben, um das Dialogfeld **Öffnen mit** abzurufen, in diesem Fall für mögliche Codeansichten.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` Handler übergeben diesen Wert <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> an die Methode, um das Dialogfeld <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> **Öffnen** mit abzurufen, in diesem Fall mit möglichen Debugansichten gefüllt, die derselben Ansicht wie <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>zugeordnet sind.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` Handler übergeben diesen Wert <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> an die Methode, um das Dialogfeld **Öffnen mit** abzurufen, in diesem Fall an Formular-Designeransichten **anzuzeigen.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` Handler übergeben diesen Wert <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> an die Methode, um das Dialogfeld **Öffnen mit** abzurufen, in diesem Fall die Standard-/Primäransicht der Editorfactory.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` Handler übergeben diesen Wert <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> an die Methode, um das Dialogfeld **Öffnen** mit abzurufen, in diesem Für eine Dokument- oder Datentexteditoransicht.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` Handler übergeben diesen Wert <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> an die Methode, die den Benutzer auffordert, auszuwählen, welche benutzerdefinierte Ansicht verwendet werden soll.|

## <a name="editor-factory-flags"></a>Editor Factory Flags

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Ein veraltetes Flag, das bitweise <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> als erster Parameter der Methode kombiniert wurde.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Kombiniert bitweise als erster <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>Parameter der ,-Methode, bedeutet dies, dass die Editorfactory die erforderlichen Korrekturen durchführen sollte.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Dieses Flag wird als erster <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Parameter der Methode bitweise kombiniert und schließt sich CEF gegenseitig [aus. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Leise](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Als erster Parameter der Methode <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> bitweise kombiniert, bedeutet dies, dass die Editorfactory den Editor erstellen sollte, ohne eine Benutzeroberfläche anzuzeigen.|

## <a name="visual-studio-errors"></a>Visual Studio-Fehler

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Eine Konstante, die von Schnittstellen zu asynchronem Verhalten zurückgegeben wird, wenn das betreffende Objekt bereits ausgelastet ist|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ein Fehler HRESULT, der für Visual Studio für "Inkompatible Dokumentdaten" spezifisch ist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und auf "Paket nicht geladen" hinweist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und angibt, dass das Projekt bereits vorhanden ist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und auf "Projektkonfiguration fehlgeschlagen" hinweist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und auf "Projekt nicht geladen" hinweist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und auf "Lösung bereits geöffnet" hinweist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und auf "Lösung nicht geöffnet" hinweist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Wird von Buildschnittstellen zurückgegeben, die Parameter zum <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> Angeben eines Arrays von der Schnittstelle haben, aber die Implementierung kann die Methode nur auf alle Ausgaben anwenden.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode gibt diesen Wert zurück, wenn das Dokument ein Format hat, das im Editor nicht geöffnet werden kann.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Ein HRESULT-Wert, der angibt, dass der Benutzer in einem Visual Studio-Assistenten auf die Schaltfläche "Zurück" drückt.|

## <a name="visual-studio-constants"></a>Visual Studio-Konstanten

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ein Fehler HRESULT, der für Visual Studio spezifisch ist und auf "Projekt weitergeleitet" hinweist.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Eine Konstante, die für Visual Studio für einen "Toolbox-Marker" spezifisch ist.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Eine Konstante, die für Visual Studio spezifisch <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> ist, um eine Benachrichtigung über die Methode zu senden, die den Beginn der Modalität angibt.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Eine Konstante, die für Visual Studio spezifisch <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> ist, um eine Benachrichtigung über die Methode zu senden, die das Ende der Modalität angibt.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Eine Konstante, die für Visual Studio spezifisch <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> ist, um eine Benachrichtigung über die Methode zu senden, die angibt, dass sich die Befehlsleistenmetriken geändert haben.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Eine für Visual Studio spezifische Konstante, die angibt, dass kein Cookie festgelegt wurde.|
|[Vsitemid. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Ein Visual Studio-Elementbezeichner, der das Fehlen eines Projektelements darstellt. Dieser Wert wird verwendet, wenn keine aktuelle Auswahl vorhanden ist.|
|[Vsitemid. wurzel](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Ein Visual Studio-Elementbezeichner, der den Stamm einer Projekthierarchie darstellt und zum Identifizieren der gesamten Hierarchie im Gegensatz zu einem einzelnen Element verwendet wird.|
|[Vsitemid. Auswahl](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Ein Visual Studio-Elementbezeichner, der das aktuell ausgewählte Element oder die aktuell ausgewählten Elemente darstellt, die den Stamm der Hierarchie enthalten können.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Beschreibt, welche Komponente der IDE gerade <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> ausgewählt wurde, z. B. in einem Aufruf.

|Konstante|Wert|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Konstanten, die verwendet werden, um einen neuen Auswahlstatus anzugeben.

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

## <a name="component-selector-dialog-constants"></a>Komponentenauswahl-Dialogkonstanten

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

## <a name="see-also"></a>Weitere Informationen

- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

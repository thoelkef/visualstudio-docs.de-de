---
title: IDE-Konstanten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18256996d829d34117caa11f4e581d8e54d738b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204042"
---
# <a name="ide-constants"></a>IDE-Konstanten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die <xref:Microsoft.VisualStudio.VSConstants> -Klasse stellt Konstanten bereit, die für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) spezifisch sind und zuvor nur in Header Dateien definiert wurden.  
  
## <a name="logical-and-physical-views"></a>Logische und physische Sichten  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|[LOGVIEWID_Code_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.code_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`Handler sollten diesen Wert an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode übergeben, um das Dialogfeld **Öffnen mit** zu erhalten, in diesem Fall bei möglichen Code Ansichten.|  
|[LOGVIEWID_Debugging_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.debugging_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`Handler übergeben diesen Wert an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um das Dialogfeld **Öffnen mit aufzurufen** , in diesem Fall mit möglichen <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> debugansichten aufgefüllt, die derselben Ansicht wie zugeordnet werden <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|  
|[LOGVIEWID_Designer_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.designer_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`Handler übergeben diesen Wert an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um das Dialogfeld **Öffnen mit** zu erhalten, in diesem Fall zum **Anzeigen von Formular** -Designer-Ansichten.|  
|[LOGVIEWID_Primary_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.primary_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`Handler übergeben diesen Wert an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um das Dialogfeld **Öffnen mit** zu erhalten, in diesem Fall die standardmäßige/primäre Ansicht der Editorfactory.|  
|[LOGVIEWID_TextView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.textview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`Handler übergeben diesen Wert an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um das Dialogfeld **Öffnen mit** zu erhalten, in dem für eine Dokument-oder Datentext-Editor-Ansicht.|  
|[LOGVIEWID_UserChooseView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.userchooseview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`Handler übergeben diesen Wert an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, die den Benutzer auffordert, die zu verwendende benutzerdefinierte Ansicht auszuwählen.|  
  
## <a name="editor-factory-flags"></a>Editorfactory-Flags  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|[CEF. Clonefile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Ein veraltetes Flag, das bitweise als erster Parameter der- <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode kombiniert ist.|  
|[CEF. Clonefile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Kombinierter bitweiser als erster Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode, gibt an, dass die Editorfactory erforderliche Korrekturen durchführen soll.|  
|[CEF. Clonefile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Kombinierter bitweiser als erster Parameter der- <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode. dieses Flag schließt [CEF aus. "Clonefile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)".|  
|[CEF. Clonefile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Kombinierter bitweiser als erster Parameter der- <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode. Dies gibt an, dass die Editorfactory den Editor ohne Anzeige einer Benutzeroberfläche (UI) erstellen soll.|  
  
## <a name="visual-studio-errors"></a>Visual Studio-Fehler  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Eine Konstante, die von Schnittstellen zum asynchronen Verhalten zurückgegeben wird, wenn das betreffende Objekt bereits ausgelastet ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ein HRESULT-Fehler, der in Visual Studio für "inkompatible Dokument Daten" spezifisch ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist, und der angibt, dass das Paket nicht geladen wurde.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist und angibt, dass das "Projekt bereits vorhanden" ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist, und der angibt, dass die Projekt Konfiguration fehlgeschlagen ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist, und der angibt, dass das Projekt nicht geladen wurde.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist, und der angibt, dass die Projekt Mappe bereits geöffnet ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist, und der angibt, dass die Projekt Mappe nicht geöffnet ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Wird von Build-Schnittstellen zurückgegeben, die über Parameter zum Angeben eines Arrays aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> Schnittstelle verfügen, aber die Implementierung kann die Methode nur auf alle Ausgaben anwenden.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Die- <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode gibt diesen Wert zurück, wenn das Dokument ein Format hat, das im Editor nicht geöffnet werden kann.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Ein HRESULT-Wert, der angibt, dass der Benutzer in einem Visual Studio-Assistenten auf die Schaltfläche "zurück" klickt.|  
  
## <a name="visual-studio-constants"></a>Visual Studio-Konstanten  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ein HRESULT-Fehler, der spezifisch für Visual Studio ist und "Projekt weitergeleitet" anzeigt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Eine-Konstante, die für Visual Studio für einen "Toolbox Marker" spezifisch ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Eine-Konstante, die für Visual Studio spezifisch ist, um eine Benachrichtigungs Meldung über die-Methode zu senden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> , die den Anfang der Modalität angibt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Eine-Konstante, die für Visual Studio spezifisch ist, um eine Benachrichtigungs Meldung über die-Methode zu senden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> , die das Ende der Modalität angibt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Eine-Konstante, die für Visual Studio spezifisch ist, um eine Benachrichtigungs Meldung über die-Methode zu senden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> , die angibt, dass sich die Metriken der Befehlsleiste|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Eine-Konstante, die für Visual Studio spezifisch ist und angibt, dass ein Cookie nicht festgelegt wurde.|  
|[VSITEMID. Trägers](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Ein Visual Studio-Element Bezeichner, der das Fehlen eines Projekt Elements darstellt. Dieser Wert wird verwendet, wenn keine aktuelle Auswahl vorliegt.|
|[VSITEMID. Fasst](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Ein Visual Studio-Element Bezeichner, der den Stamm einer Projekt Hierarchie darstellt und verwendet wird, um die gesamte Hierarchie zu identifizieren, im Gegensatz zu einem einzelnen Element.|
|[VSITEMID. End](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Ein Visual Studio-Element Bezeichner, der das aktuell ausgewählte Element bzw. die Elemente darstellt, die den Stamm der Hierarchie enthalten können.| 
  
## <a name="ivsselectionevents"></a>IVsSelectionEvents  
 Beschreibt, welche Komponente der IDE soeben in einem-Beispiel ausgewählt wurde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> .  
  
|Konstante|Wert|
|--------------|-----------|
|[SelectionElement.Documentframe](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[Selectionelement. propertybrowsersid](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[Selectionelement. StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[Selectionelement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[Selectionelement. userContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[Selectionelement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1| 
  
## <a name="vsselelemid"></a>VSSELELEMID  
 Konstanten, die zum Angeben eines neuen Auswahl Zustands verwendet werden.  
  
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
  
## <a name="component-selector-dialog-constants"></a>Komponentenauswahl-Dialog Konstanten  
  
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
 [IDE-definierte Befehle zum Erweitern von Projektsystemen](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

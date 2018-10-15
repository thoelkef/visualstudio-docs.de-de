---
title: IDE-Konstanten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 44058a483e4181b7f1918b63c844b2bb4345c89c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236430"
---
# <a name="ide-constants"></a>IDE-Konstanten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die <xref:Microsoft.VisualStudio.VSConstants> Klasse enthält die Konstanten, die die integrierte Entwicklungsumgebung (IDE) spezifisch sind und, die zuvor nur in Headerdateien definiert wurden.  
  
## <a name="logical-and-physical-views"></a>Logische und physische Ansichten  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|[LOGVIEWID_Code_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.code_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler sollten diesen Wert zum Übergeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall auf möglichen Codeansichten.|  
|[LOGVIEWID_Debugging_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.debugging_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall gefüllt mit möglichen <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> Debug-Ansichten, die zur gleichen Ansicht wie ordnen <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|  
|[LOGVIEWID_Designer_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.designer_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall um **Formular anzeigen** -Designer-Ansichten.|  
|[LOGVIEWID_Primary_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.primary_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall die standardmäßige/primäre Ansicht der Editorfactory.|  
|[LOGVIEWID_TextView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.textview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> -Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall für ein Dokument oder -Text-Editor-Ansicht.|  
|[LOGVIEWID_UserChooseView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.userchooseview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergibt diesen Wert als die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, die den Benutzer auffordert, welche benutzerdefinierte Ansicht verwendet.|  
  
## <a name="editor-factory-flags"></a>Editor-Factory-Flags  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Ein veraltetes Flag bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode.|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, Methode, dies weist darauf hin Editorfactory sollte die notwendigen Korrekturen durchführen.|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> -Methode, dieses Flag schließen sich gegenseitig aus der [CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015).|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Bitweise kombiniert als der erste Parameter der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> -Methode, dies gibt die Editorfactory sollte den Editor erstellen, ohne eine Benutzeroberfläche (UI) anzuzeigen.|  
  
## <a name="visual-studio-errors"></a>Visual Studio-Fehler  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Eine Konstante, die von Schnittstellen zurückgegeben werden, um asynchrones Verhalten bei der das Objekt bereits ausgelastet ist|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Fehler HRESULT, das speziell für Visual Studio für "nicht kompatible Dokumentendaten" ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Fehler HRESULT, das für Visual Studio, und dass angibt "Paket nicht geladen."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Fehler HRESULT, das für Visual Studio und, gibt an, dass die "Projekt bereits vorhanden."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Fehler HRESULT, das speziell für Visual Studio und, der angibt, "Projektkonfiguration fehlgeschlagen".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Fehler HRESULT, das für Visual Studio, und dass angibt "Projekt nicht geladen."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Fehler HRESULT, das für Visual Studio und, gibt an, "Projektmappe bereits geöffnet."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Fehler HRESULT, das speziell für Visual Studio und, der angibt, "Projektmappe nicht geöffnet werden."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Die von der buildschnittstellen, die Parameter zum Angeben eines Arrays von haben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> -Schnittstelle, aber die Implementierung der Methode nur auf alle Ausgaben anwenden kann.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode gibt diesen Wert zurück, wenn das Dokument ein Format hat, die im Editor nicht geöffnet werden kann.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Ein HRESULT-Wert, der angibt, dass der Benutzer die Schaltfläche "zurück", in einem Visual Studio-Assistenten geklickt.|  
  
## <a name="visual-studio-constants"></a>Visual Studio-Konstanten  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Fehler HRESULT, das für Visual Studio, und dass angibt "Projekt weitergeleitet".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Eine Konstante, die speziell für Visual Studio für einen "toolboxmarker".|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Eine Konstante, die speziell für Visual Studio ist für die Übertragung einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die den Anfang der Modalität angibt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Eine Konstante, die speziell für Visual Studio ist für die Übertragung einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die das Ende der Modalität angibt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Eine Konstante, die speziell für Visual Studio ist für die Übertragung einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die angibt, dass sich die befehlsleistenmetrik geändert haben.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Eine Konstante, die speziell für Visual Studio ist, der angibt, dass ein Cookie nicht festgelegt wurde.|  
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Eine Visual Studio-Element-ID, die das Fehlen eines Projektelements darstellt. Dieser Wert wird verwendet, wenn keine aktuelle Auswahl vorhanden ist.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Eine Visual Studio-Element-ID, die den Stamm einer Projekthierarchie darstellt und wird verwendet, um die gesamte Hierarchie, im Gegensatz zu einem einzelnen Element zu identifizieren.|
|[VSITEMID. Auswahl](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Eine Visual Studio-Element-ID, die darstellt, die aktuell ausgewählte Element oder Elemente, die den Stamm der Hierarchie enthalten können.| 
  
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
 [IDE-definierte Befehle zum Erweitern von Projektsystemen](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)


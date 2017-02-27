---
title: "IDE-Konstanten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fehler-IDE"
  - "logische Ansichten"
  - "IDE-Fehler [Visual Studio]"
  - "UI-Kontext-Konstanten"
  - "Konstanten, die Visual Studio-IDE"
  - "IDE-Konstanten"
  - "physische Ansichten"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# IDE-Konstanten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die <xref:Microsoft.VisualStudio.VSConstants> Klasse enthält Konstanten, die auf der integrated Development Environment \(IDE\) spezifisch sind und, die zuvor nur in den Headerdateien definiert wurden.  
  
## Logische und physische Ansichten  
  
|Wert|Beschreibung|  
|----------|------------------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler sollte übergeben Sie diesen Wert auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall auf mögliche Code\-.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergeben Sie diesen Wert auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall mit möglichen gefüllt <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> Debuggen von Ansichten, die auf die gleiche Ansicht zuordnen <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergeben Sie diesen Wert auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall um **Formular anzeigen** Designeransichten.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergeben Sie diesen Wert auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode zum Abrufen der **Öffnen mit** Dialogfeld, in diesem Fall die Standard oder primäre Ansicht der\-Editor\-Factory.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergeben Sie diesen Wert auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode zum Abrufen der **Öffnen mit** Sie im Dialogfeld für ein Dokument oder eine Datendatei Text\-Editor anzeigen.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` Handler übergeben Sie diesen Wert auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, die den Benutzer auffordert, wählen Sie die benutzerdefinierte Ansicht verwenden.|  
  
## Editor\-Factory\-Flags  
  
|Wert|Beschreibung|  
|----------|------------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|Eine veraltete Flag kombiniert bitweise als erster Parameter von der <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|Als der erste Parameter der bitweise kombiniert die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, Methode Hiermit\-Editor\-Factory sollten die erforderlichen Korrekturen durchführen.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|Als der erste Parameter der bitweise kombiniert die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode dieses Flag schließen sich gegenseitig aus der <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|Als der erste Parameter der bitweise kombiniert die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Methode Hiermit\-Editor\-Factory sollten Editor erstellen, ohne eine Benutzeroberfläche \(UI\).|  
  
## Visual Studio\-Fehler  
  
|Wert|Beschreibung|  
|----------|------------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Eine Konstante, die das asynchrone Verhalten von Schnittstellen zurückgegebene bei dem betreffenden Objekt bereits gebucht|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für "Dokumentdaten nicht kompatibel".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die angibt, dass "Paket nicht geladen."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und angibt, dass die "Projekt existiert bereits."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und, der angibt, "Konfiguration des Projekts Fehler."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die angibt, dass "\-Projekt nicht geladen."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die angibt, dass "Lösung bereits geöffnet."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die angibt, dass "Lösung nicht öffnen."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Zurückgegebene von Build\-Schnittstellen, die die Parameter für die Angabe eines Arrays aus haben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> \-Schnittstelle, aber die Implementierung der Methode nur auf alle Ausgaben anwenden kann.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Die <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \-Methode gibt diesen Wert zurück, wenn das Dokument ein Format aufweist, die im Editor nicht geöffnet werden kann.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Ein HRESULT\-Wert, der angibt, dass der Benutzer die zurück\-Schaltfläche in erreicht eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Assistenten.|  
  
## Visual Studio\-Konstanten  
  
|Wert|Beschreibung|  
|----------|------------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ein Fehler\-HRESULT, das für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und, der angibt, "Project weitergeleitet."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Eine Konstante, die für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für ein "Toolbox"Marker.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Eine Konstante, die für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für das Senden einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die den Anfang des Modalität angibt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Eine Konstante, die für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für das Senden einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die das Ende des Modalität angibt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Eine Konstante, die für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für das Senden einer Benachrichtigung über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Methode, die angibt, dass die Befehl Balken Metriken geändert haben.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Eine Konstante, die für spezifische [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] der angibt, dass ein Cookie nicht festgelegt wurde.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Element\-ID, die das Fehlen eines Projektelements darstellt. Dieser Wert wird verwendet, wenn keine aktuelle Auswahl vorhanden ist.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Element\-ID, die stellt den Stamm einer Projekthierarchie dar und wird verwendet, um die gesamte Hierarchie, im Gegensatz zu einem einzelnen Element zu identifizieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|Ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Element\-ID, das das aktuell ausgewählte Element oder Elemente, z. den Stamm der Hierarchie b. darstellt.|  
  
## IVsSelectionEvents  
 Beschreibt, welche Komponente der IDE einfach, in ausgewählt wurde ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> aufrufen, z. B..  
  
|Konstante|Wert|  
|---------------|----------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0 x 2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0 x 4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0 x 3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0 x 0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0 x 5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0 x 1|  
  
## VSSELELEMID  
 Konstanten verwendet, um einen neuen Auswahlstatus anzuzeigen.  
  
|Konstante|Wert|  
|---------------|----------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## Konstanten der Komponente Selector\-Dialogfeld  
  
|Konstante|Wert|  
|---------------|----------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER \+ 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER \+ 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER \+ 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER \+ 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER \+ 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER \+ 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER \+ 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER \+ 1289|  
  
## Siehe auch  
 [IDE\-definierte Befehle für die Erweiterung Projektsysteme](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
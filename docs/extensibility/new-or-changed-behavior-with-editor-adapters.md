---
title: Neue oder geänderte Verhalten mit dem Editor Adapter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22028b1b2725f184c3d5748f2885a17d4bff0c60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148661"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Neue oder geänderte Verhalten mit Editor-Adaptern
Wenn aktualisiert werden soll, Code, die auf früheren Versionen von Visual Studio Core Editor geschrieben wurde, und Sie die Editor-Adapter (oder Shims) statt der neuen API verwenden möchten, sollten Sie beachten Sie die folgenden Unterschiede im Verhalten der Editor Adapter sein. in Bezug auf den vorherigen Core-Editor.  
  
## <a name="features"></a>Features  
  
#### <a name="using-setsite"></a>Verwenden von SetSite()  
 Rufen Sie <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> beim CoCreate Textpuffer, Text-Ansichten und Codefenster, bevor Sie andere Vorgänge auf ihnen ausführen. Dies ist jedoch nicht erforderlich, wenn Sie mithilfe der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , erstellen, da dieser Dienst Create()-Methoden selbst aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosten von IVsCodeWindow und IVsTextView in Ihre eigenen Inhalte  
 Sie können beide hosten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in Ihre eigenen Inhalte mithilfe von Win32-Modus oder WPF-Modus. Sie sollten jedoch berücksichtigt werden, dass einige Unterschiede in zwei Modi vorhanden sind.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Win32- und WPF-Versionen der IVsCodeWindow  
 Der Code-Editorfenster abgeleitet <xref:Microsoft.VisualStudio.Shell.WindowPane>, implementiert die ältere Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> sowie das neue WPF-Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> Schnittstelle. Können Sie die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> Methode, um ein HWND-basierte Hostingumgebung zu erstellen oder die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> Methode, um eine WPF-Hostingumgebung zu erstellen. Der zugrunde liegenden-Editor verwendet immer WPF, aber Sie können die Art der Fensterbereich, die Ihrer hostinganforderungen passt, wenn Sie diesen Fensterbereich direkt in Ihre eigenen Inhalte einbetten erstellen.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Win32- und WPF-Versionen der IVsTextView  
 Sie können festlegen, eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf Win32- oder WPF-Modus.  
  
 Wenn eine Editorfactory eine Textansicht standardmäßig erstellt er wird in einem HWND gehostet und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> gibt einen HWND zurück. Sie sollten in diesem Modus nicht verwenden, um den Editor in einem WPF-Steuerelement einzubetten.  
  
 Um eine Textansicht in WPF-Modus zu versetzen, rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> und übergeben Sie <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> wie eines der Initialisierung in kennzeichnet die `InitView` Parameter. Sie erhalten die <xref:System.Windows.FrameworkElement> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 WPF-Modus unterscheidet sich von Win32-Modus auf zwei Arten. Erstens kann Textansicht in einem WPF-Kontext gehostet werden. Sie können den WPF-Bereich zugreifen, durch Umwandlung der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> und Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Zweitens <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> noch zurück, die einem HWND, aber diese HWND kann nur zum Überprüfen seiner Position und Festlegen des Fokus darauf verwendet werden. Diese HWND müssen können nicht so reagieren Sie auf eine WM_PAINT-Meldung, da es nicht auswirkt, wie der Editor des Fensters zeichnet. Diese HWND ist vorhanden, nur für den Übergang zu den neuen EditorCode mithilfe der Adapter zu erleichtern. Es wird dringend empfohlen, dass Sie nicht verwenden sollten `VIF_NO_HWND_SUPPORT` , wenn die Komponente einen HWND funktioniert, und aufgrund von Beschränkungen im Merry HWND erfordert `GetWindowHandle` während Sie sich in diesem Modus.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Übergeben von Arrays als Parameter in systemeigenem code  
 Es gibt viele Methoden in die legacy-Editor-API, die über Parameter verfügen, die ein Array handelt sowie der Anzahl enthalten. Beispiele sind:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Wenn Sie diese Methoden in systemeigenem Code aufrufen, müssen Sie jeweils nur ein Element übergeben. Wenn Sie mehr als ein Element übergeben, wird der Aufruf aufgrund von Problemen mit der primären Interop-Implementierung, zurückgewiesen.  
  
 Das Problem ist komplexer mit Methoden wie z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Jedes Mal, wenn diese Methode aufgerufen wird, löscht es die vorherige Liste der ignorierten Markertypen, daher es nicht möglich ist einfach ist, diese Methode mit drei verschiedenen Markertypen dreimal aufgerufen. Die einzige Lösung wird diese Methode nur in verwaltetem Code aufzurufen.  
  
#### <a name="threading"></a>Threading  
 Sie sollten immer den Puffer Adapter vom UI-Thread aufrufen. Der Puffer-Adapter ist ein verwaltetes Objekt, das bedeutet, dass er aus verwaltetem Code Aufrufen die COM-Marshalling umgehen, und Ihrem Aufruf automatisch nicht an den UI-Thread gemarshallt werden wird.  Wenn Sie den Adapter Puffer aus einem Hintergrundthread aufrufen, müssen Sie verwenden <xref:System.Windows.Threading.Dispatcher.Invoke%2A> oder eine ähnliche Methode.  
  
#### <a name="lockbuffer-methods"></a>LockBuffer-Methoden  
 Alle LockBuffer()-Methoden sind veraltet. Beispiele sind:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Commit-Ereignisse  
 Commit-Ereignisse werden nicht unterstützt. Aufrufen einer Methode, die anweist, für diese Ereignisse bewirkt, dass die Methode einen Fehlercode zurückgegeben.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 Die <xref:EnvDTE.TextEditorEvents> auf Commit() nicht mehr ausgelöst werden. Stattdessen werden diese bei jeder textänderung ausgelöst.  
  
#### <a name="text-markers"></a>Text-Marker  
 Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Objekte, wenn Sie diese entfernen. In früheren Versionen mussten Sie nur die Marker freizugeben.  
  
#### <a name="line-numbers"></a>Zeilennummern  
 Für eine Vielzahl von Methoden auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, Zeilennummern zugrunde liegenden Puffer Zeilennummern entsprechen, keine Zeilennummern dieser Faktor bei der Gliederung und Zeilenumbruch, wie in Visual Studio 2008.  
  
 Die Methoden, die betroffenen gehören (die Liste ist nicht vollständig):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Gliedern  
 Clients des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> sehen nur die Gliederungsbereiche, die hinzugefügt wurden, mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>oder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Es werden ad-hoc-Regionen nicht angezeigt, da sie nicht über die Editor-Adapter hinzugefügt werden. Ebenso werden diese Clients nicht angezeigt Gliederungsbereiche Programmiersprachen (z. B. c# und C++), mit dem der neue EditorCode anstatt die Editor-Adapter, hinzugefügt.  
  
#### <a name="line-heights"></a>Höhe der Zeile  
 In den neuen Editor möglich Textzeilen unterschiedliche Höhen, abhängig von der Schriftgröße und mögliche Zeilentransformationen, die die Zeile relativ zu anderen Positionen verschieben können. Die Höhe einer Zeile von Methoden zurückgegeben, wie z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> die Höhe einer Textzeile, verwenden die Standardschriftgröße mit keine Zeilentransformationen angewendet wird. Diese Höhe bzw. entsprechen möglicherweise nicht die tatsächliche Höhe einer Textzeile in der Ansicht.  
  
#### <a name="eventing-and-undo"></a>Ereignisse und Rückgängigmachen  
 Die Sicht weiterhin in den neuen Editor Vorgänge wie das Rendern und Auslösen von Ereignissen kontinuierlich, selbst wenn ein Rückgängig-Cluster geöffnet ist. Dieses Verhalten unterscheidet sich von dem der ältere Ansichten, die nicht diese Vorgänge erst nach dem Schließen des Rückgängig-Clusters ausgeführt haben.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Methode schlägt fehl, wenn Sie in einer Klasse übergeben, das keine entweder implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> oder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Benutzerdefinierte Win32 Ownerdrawn-Popups werden nicht mehr unterstützt.  
  
#### <a name="smarttags"></a>SmartTags  
 Es gibt keine Adapter-Unterstützung für Smarttags erstellt, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> Schnittstellen.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Ist nicht implementiert.  
  
## <a name="unimplemented-methods"></a>Nicht implementierte Methode  
 Einige Methoden wurden nicht auf den Text-Puffer-Adapter, Text anzeigen und Text Ebene Adapter implementiert.  
  
|Interface|Nicht implementiert.|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Ist nicht implementiert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> wird in den Adaptern jedoch ignoriert, über die Gliederung Benutzeroberfläche implementiert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> wird in den Adaptern jedoch ignoriert, über die Gliederung Benutzeroberfläche implementiert.|
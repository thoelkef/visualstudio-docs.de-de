---
title: Neues oder geändertes Verhalten mit Editor Adaptern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194176"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Neues oder geändertes Verhalten bei Editor-Adaptern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Code aktualisieren, der für frühere Versionen von Visual Studio-Kern-Editor geschrieben wurde, und Sie beabsichtigen, die Editor Adapter (oder Shims) zu verwenden, anstatt die neue API zu verwenden, sollten Sie die folgenden Unterschiede im Verhalten der Editor-Adapter in Bezug auf den vorherigen Kern-Editor beachten.  
  
## <a name="features"></a>Features  
  
#### <a name="using-setsite"></a>Verwenden von SetSite ()  
 Sie müssen aufrufen <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> , wenn Sie Text Puffer, Text Ansichten und Code Fenster erstellen, bevor Sie andere Vorgänge ausführen. Dies ist jedoch nicht erforderlich, wenn Sie verwenden <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , um Sie zu erstellen, da die Create ()-Methode dieses dienstangs selbst aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosten von IVsCodeWindow und IVsTextView in ihren eigenen Inhalten  
 Sie können sowohl <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> als auch <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in Ihrem eigenen Inhalt mit dem Win32-Modus oder dem WPF-Modus hosten. Beachten Sie jedoch, dass es einige Unterschiede zwischen den beiden Modi gibt.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Verwenden von Win32-und WPF-Versionen von IVsCodeWindow  
 Das Editor-Code Fenster wird von abgeleitet <xref:Microsoft.VisualStudio.Shell.WindowPane> , das sowohl die ältere Win32- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle als auch die neue WPF- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> Schnittstelle implementiert. Sie können die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> -Methode verwenden, um eine HWND-basierte Hostingumgebung oder die- <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> Methode zum Erstellen einer WPF-Hostingumgebung zu erstellen. Der zugrunde liegende Editor verwendet immer WPF. Sie können jedoch den Fensterbereich erstellen, der Ihren hostinganforderungen entspricht, wenn Sie diesen Fensterbereich direkt in ihren eigenen Inhalt einbetten.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Verwenden von Win32-und WPF-Versionen von IVsTextView  
 Sie können <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für den Win32-Modus oder den WPF-Modus festlegen.  
  
 Wenn eine Editorfactory eine Textansicht erstellt, wird Sie standardmäßig in einem HWND gehostet und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> gibt ein HWND zurück. Sie sollten diesen Modus nicht verwenden, um den Editor in ein WPF-Steuerelement einzubetten.  
  
 Um eine Textansicht auf den WPF-Modus festzulegen, müssen Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> als eine der Initialisierungsflags im- `InitView` Parameter übergeben. Sie können das <xref:System.Windows.FrameworkElement> abrufen, indem Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 Der WPF-Modus unterscheidet sich auf zwei Arten vom Win32-Modus. Zuerst kann die Textansicht in einem WPF-Kontext gehostet werden. Sie können auf den WPF-Bereich zugreifen, indem Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in umwandeln <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> und aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . Zweitens <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> gibt immer noch ein HWND zurück, aber dieses HWND kann nur verwendet werden, um seine Position zu überprüfen und den Fokus darauf festzulegen. Dieses HWND darf nicht verwendet werden, um auf eine WM_PAINT Nachricht zu reagieren, da es sich nicht darauf auswirkt, wie der Editor das Fenster zeichnet. Dieses HWND ist nur vorhanden, um den Übergang zum neuen Editor-Code mithilfe der Adapter zu vereinfachen. Es wird dringend empfohlen, dass Sie nicht verwenden `VIF_NO_HWND_SUPPORT` , wenn die Komponente ein HWND benötigt, da die Einschränkungen in dem HWND, das von der `GetWindowHandle` Zeit in diesem Modus zurückgegeben wurde, erforderlich sind.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Übergeben von Arrays als Parameter in nativem Code  
 Es gibt viele Methoden in der Legacy-Editor-API mit Parametern, die ein Array und seine Anzahl enthalten. Beispiele:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Wenn Sie diese Methoden in nativem Code aufrufen, müssen Sie nur jeweils ein Element übergeben. Wenn Sie mehr als ein Element übergeben, wird der-Rückruf aufgrund von Problemen mit der primären Interop-Implementierung zurückgewiesen.  
  
 Das Problem ist mit Methoden wie komplexer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Jedes Mal, wenn diese Methode aufgerufen wird, wird die vorherige Liste der ignorierten Markertypen gelöscht. Daher ist es nicht möglich, diese Methode dreimal mit drei verschiedenen Markertypen aufzurufen. Die einzige Abhilfe besteht darin, diese Methode nur in verwaltetem Code aufzurufen.  
  
#### <a name="threading"></a>Threading  
 Der Puffer Adapter sollte immer aus dem UI-Thread aufgerufen werden. Der Puffer Adapter ist ein verwaltetes Objekt, d. h., dass der Aufruf aus verwaltetem Code das COM-Marshalling umgeht und Ihr Aufruf nicht automatisch an den UI-Thread gemarshallt wird.  Wenn Sie den Puffer Adapter von einem Hintergrund Thread aus aufrufen, müssen Sie <xref:System.Windows.Threading.Dispatcher.Invoke%2A> oder eine ähnliche Methode verwenden.  
  
#### <a name="lockbuffer-methods"></a>LockBuffer-Methoden  
 Alle LockBuffer ()-Methoden sind veraltet. Beispiele:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Commit-Ereignisse  
 Commit-Ereignisse werden nicht unterstützt. Das Aufrufen einer Methode, die diese Ereignisse anrät, bewirkt, dass die Methode einen Fehlercode zurückgibt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>Texteditor Events  
 Der wird <xref:EnvDTE.TextEditorEvents> bei Commit () nicht mehr ausgelöst. Stattdessen werden Sie für jede Textänderung ausgelöst.  
  
#### <a name="text-markers"></a>Text Marker  
 Sie müssen für-Objekte aufzurufen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Wenn Sie Sie entfernen. In früheren Versionen mussten nur die Marker freigegeben werden.  
  
#### <a name="line-numbers"></a>Zeilennummern  
 Für eine Vielzahl von Methoden in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> entsprechen Zeilennummern den zugrunde liegenden Puffer Zeilennummern, nicht von Zeilennummern, die die Gliederung und den Zeilenumbruch berücksichtigen, wie in Visual Studio 2008.  
  
 Folgende Methoden sind betroffen (die Liste ist nicht vollständig):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Gliedern  
 Clients von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> sehen nur die Gliederungs Bereiche, die mithilfe von oder hinzugefügt wurden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Die Ad-hoc-Regionen werden nicht angezeigt, da Sie nicht über die Editor Adapter hinzugefügt werden. Ebenso sehen diese Clients keine Gliederungs Bereiche, die von Sprachen hinzugefügt werden (einschließlich c# und C++), die den neuen Editor-Code anstelle der Editor-Adapter verwenden.  
  
#### <a name="line-heights"></a>Linien Höhen  
 Im neuen Editor können Textzeilen je nach Schriftart Größe und möglichen Linien Transformationen, die die Linie relativ zu anderen Zeilen verschieben können, unterschiedlich sein. Die Zeilenhöhe, die von Methoden wie zurückgegeben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> wird, ist die Höhe einer Zeile mit dem Standardschrift Grad ohne angewendete Zeilen Transformationen. Diese Höhe kann die tatsächliche Höhe einer Zeile in der Ansicht widerspiegeln.  
  
#### <a name="eventing-and-undo"></a>Ereignisse und Rückgängigmachen  
 Im neuen Editor führt die Ansicht weiterhin Vorgänge aus, z. b. das Rendern und das Ausgeben von Ereignissen, auch wenn ein rückgängig-Cluster geöffnet ist. Dieses Verhalten unterscheidet sich von älteren Sichten, die diese Vorgänge erst nach dem Schließen des rückgängig-Clusters durchgeführt haben.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- Bei der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Methode tritt ein Fehler auf, wenn Sie eine Klasse übergeben, die weder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> noch implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Von benutzerdefinierten Win32-Besitzern gezeichnete Popups werden nicht mehr unterstützt.  
  
#### <a name="smarttags"></a>Von Smarttags  
 Es gibt keine Adapter Unterstützung für Smarttags, die mit den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> Schnittstellen,, und erstellt wurden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> ist nicht implementiert.  
  
## <a name="unimplemented-methods"></a>Nicht implementierte Methoden  
 Einige Methoden wurden auf dem Text Puffer Adapter, dem Text Ansichts Adapter und dem Text Schicht Adapter nicht implementiert.  
  
|Schnittstelle|Nicht implementiert|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` ist nicht implementiert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> wird in den Adaptern implementiert, aber von der Gliederungs Benutzeroberfläche ignoriert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> wird in den Adaptern implementiert, aber von der Gliederungs Benutzeroberfläche ignoriert.|

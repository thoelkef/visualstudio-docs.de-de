---
title: Neues oder Geändertes Verhalten mit Editor-Adaptern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce1cc8c95fcd2c6a34342b71c1c94bf5930e0e51
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521399"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Neues oder Geändertes Verhalten mit Editor-Adaptern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [neues oder Geändertes Verhalten mit Editor-Adaptern](https://docs.microsoft.com/visualstudio/extensibility/new-or-changed-behavior-with-editor-adapters).  
  
Wenn Sie planen, die Editor-Adapter (oder Shims) verwenden, anstatt die neue API aktualisieren Sie Code, der auf früheren Versionen von Visual Studio-Kern-Editor geschrieben wurde, sollten Sie beachten Sie die folgenden Unterschiede im Verhalten der Editor für Adapter sein. in Bezug auf die vorherige Kern-Editor.  
  
## <a name="features"></a>Features  
  
#### <a name="using-setsite"></a>Verwenden von SetSite()  
 Rufen Sie <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> beim CoCreate Textpuffer Textansichten, und Windows programmieren, bevor Sie andere Vorgänge auf diesen ausführen. Dies ist jedoch nicht erforderlich, bei der Verwendung der <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , zu erstellen, da dieses Diensts Create() Methoden selbst aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosten von IVsCodeWindow und IVsTextView in eigener Inhalte  
 Sie können beide hosten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in Ihren eigenen Inhalt, der mit den Win32- oder WPF-Modus. Allerdings sollten Sie bedenken, dass es einige Unterschiede in den beiden Modi.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Mithilfe von Win32 und WPF-Versionen von IVsCodeWindow  
 Der Code-Editor-Fenster wird abgeleitet <xref:Microsoft.VisualStudio.Shell.WindowPane>, implementiert die ältere Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle sowie das neue WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> Schnittstelle. Können Sie die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> Methode, um ein HWND-basierte Hostingumgebung zu erstellen oder die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> Methode zum Erstellen einer WPF-hosting-Umgebung. Der zugrunde liegenden Editor immer verwendet WPF, aber Sie können die Art des Fensterbereichs, der Ihrer hostinganforderungen geeignet ist, wenn Sie diesen Fensterbereich direkt in Ihre eigenen Inhalte einbetten erstellen.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Mithilfe von Win32 und WPF-Versionen von IVsTextView  
 Sie können festlegen, eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf Win32- oder WPF-Modus.  
  
 Wenn eine Editorfactory eine Textansicht erstellt standardmäßig in ein HWND, gehostet wird und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> gibt einen HWND zurück. Sie sollten nicht diesen Modus verwenden, um den Editor in einem WPF-Steuerelement einzubetten.  
  
 Um eine Textansicht in WPF-Modus festzulegen, rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> und übergeben Sie <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> wie eines der Initialisierung in Bitflags, die die `InitView` Parameter. Sie erhalten die <xref:System.Windows.FrameworkElement> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 WPF-Modus unterscheidet sich von Win32-Modus gibt es zwei Möglichkeiten. Erstens kann die Textansicht in einem WPF-Kontext gehostet werden. Sie können im WPF-Bereich zugreifen, durch das Umwandeln der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> und Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Zweitens <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> weiterhin gibt ein HWND, aber dieses HWND kann nur zum Überprüfen seiner Position und Festlegen des Fokus darauf verwendet werden. Sie müssen nicht dieses HWND verwenden, um auf eine WM_PAINT-Meldung zu reagieren, da es nicht beeinträchtigt wird, wie der Editor-Fenster zeichnet. Dieses HWND ist vorhanden, nur für den Übergang zu den neuen EditorCode mithilfe der Adapter zu erleichtern. Es wird dringend empfohlen, dass Sie nicht verwenden sollten `VIF_NO_HWND_SUPPORT` , wenn die Komponente ein HWND funktioniert, und aufgrund von Beschränkungen im Merry HWND erfordert `GetWindowHandle` während Sie sich in diesem Modus.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Übergeben von Arrays als Parameter in nativem code  
 Es gibt viele Methoden in der legacy-API-Editor, deren Parameter ein Array und der Anzahl enthalten. Beispiele sind:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Wenn Sie diese Methoden in systemeigenem Code aufrufen, müssen Sie zu einem Zeitpunkt nur ein Element übergeben. Wenn Sie in mehr als ein Element übergeben, wird der Aufruf, aufgrund von Problemen mit der primären Interop-Implementierung abgelehnt.  
  
 Das Problem ist komplexer mit Methoden wie z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Jedes Mal, wenn diese Methode aufgerufen wird, löscht es die vorherige Liste der ignorierten Markertypen, damit es nicht einfach zum Aufrufen dieser Methode drei Mal auf drei verschiedenen Markertypen möglich ist. Die einzige Lösung ist, diese Methode nur im verwalteten Code aufzurufen.  
  
#### <a name="threading"></a>Threading  
 Sie sollten immer den TextBuffer-Adapter vom UI-Thread aufrufen. Der Puffer-Adapter ist ein verwaltetes Objekt, das bedeutet, dass sie über verwalteten Code Aufrufen die COM-Marshalling umgehen, und der Aufruf automatisch nicht an den UI-Thread gemarshallt werden wird.  Wenn Sie den TextBuffer-Adapter von einem Hintergrundthread aufrufen, müssen Sie verwenden <xref:System.Windows.Threading.Dispatcher.Invoke%2A> oder einer ähnlichen Methode.  
  
#### <a name="lockbuffer-methods"></a>LockBuffer-Methoden  
 Alle LockBuffer()-Methoden sind veraltet. Beispiele sind:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Commit-Ereignisse  
 Commit Ereignisse werden nicht unterstützt. Aufrufen einer Methode, die dazu rät für diese Ereignisse bewirkt, dass die Methode einen Fehlercode zurückgibt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 Die <xref:EnvDTE.TextEditorEvents> nicht mehr auf Commit() ausgelöst werden. Stattdessen werden sie bei jeder textänderung ausgelöst.  
  
#### <a name="text-markers"></a>Textmarkierungen  
 Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Objekten, wenn Sie diese entfernen. In früheren Versionen mussten Sie nur die Marker freizugeben.  
  
#### <a name="line-numbers"></a>Zeilennummern  
 Für eine Vielzahl von Methoden für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, Zeilennummern zu entsprechen, den zugrunde liegenden Puffer Zeilennummern, nicht Zeilennummern dieser Faktor bei der Gliederung und Zeilenumbruch, wie Sie in Visual Studio 2008.  
  
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
 Clients <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> sehen nur die Gliederungsbereiche, die hinzugefügt wurden, mithilfe von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>oder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Sie können ad-hoc-Regionen werden nicht angezeigt, da sie nicht über die Editor-Adapter hinzugefügt werden. Ebenso werden diesen Clients nicht angezeigt Gliedern von Bereichen von Sprachen (einschließlich c# und C++), die der neue EditorCode statt in die Editor-Adapter verwenden, hinzugefügt.  
  
#### <a name="line-heights"></a>Höhe der Zeile  
 Im neuen Editor haben Textzeilen unterschiedlicher Höhe, je nach den Schriftgrad und mögliche Zeilentransformationen, die die Linie relativ zu anderen Positionen verschoben werden können. Die Zeilenhöhe von Methoden zurückgegeben werden beispielsweise <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> ist die Höhe einer Zeile mit der Standardschriftgrad, die keine Zeilentransformationen angewendet. Diese Höhe kann oder die tatsächliche Höhe einer Zeile in der Ansicht u. u. nicht wiedergegeben.  
  
#### <a name="eventing-and-undo"></a>Ereignisprotokollierung und rückgängig machen  
 Die Sicht weiterhin des neuen Editors ist führen Sie Vorgänge wie das rendering und Auslösen von Ereignissen kontinuierlich, selbst wenn ein Rückgängig-Cluster geöffnet ist. Dieses Verhalten unterscheidet sich von der älteren Ansichten, mit die nicht diese Vorgänge erst nach dem Schließen des Rückgängig-Clusters ausgeführt haben.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Methode schlägt fehl, wenn Sie in einer Klasse übergeben, die nicht entweder implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> oder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Benutzerdefinierte Win32-Ownerdrawn-Popups werden nicht mehr unterstützt.  
  
#### <a name="smarttags"></a>SmartTags  
 Es gibt keine Adapter-Unterstützung für Smarttags, die mit dem Sie erstellt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> Schnittstellen.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Ist nicht implementiert.  
  
## <a name="unimplemented-methods"></a>Nicht implementierte Methode  
 Einige Methoden wurden für den TextBuffer-Adapter, Textansichtsadapters und Text-Layer-Adapter nicht implementiert.  
  
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
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> wird in den Adaptern jedoch ignoriert, über die Gliederung Benutzeroberfläche implementiert werden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> wird in den Adaptern jedoch ignoriert, über die Gliederung Benutzeroberfläche implementiert werden.|


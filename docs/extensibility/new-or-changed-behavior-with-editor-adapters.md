---
title: "Neue oder ge&#228;nderte Verhalten mit Editor-Adaptern | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Verhalten des Adapters"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Neue oder ge&#228;nderte Verhalten mit Editor-Adaptern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie Code, der auf früheren Versionen von Visual Studio primären Editor geschrieben wurde aktualisieren, und Sie die Editor\-Adapter \(oder Shims\) statt der neuen API verwenden möchten, sollten Sie die folgenden Unterschiede im Verhalten der Editor\-Adapter in Bezug auf den vorherigen Core\-Editor sein.  
  
## Funktionen  
  
#### Verwenden die SetSite\(\)  
 Sie müssen Aufrufen <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> beim CoCreate Textpuffer, Text\-Ansichten und Windows code, bevor Sie alle anderen Operationen darauf ausführen. Dies ist jedoch nicht erforderlich, wenn Sie verwenden die <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> erstellen, da dieser Dienst Create\(\) Methoden selbst aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### Hosten von IVsCodeWindow und IVsTextView in Ihrer eigenen Inhalte  
 Sie können beide hosten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in Ihrer eigenen Inhalte, die mit den Win32\- oder WPF\-Modus. Allerdings sollten Sie bedenken, dass es einige Unterschiede in den beiden Modi gibt.  
  
##### Mithilfe von Win32 und WPF\-Versionen von IVsCodeWindow  
 Der Code\-Editor\-Fenster wird von abgeleitet <xref:Microsoft.VisualStudio.Shell.WindowPane>, implementiert die ältere Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> sowie das neue WPF\-Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> Schnittstelle. Können Sie die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> Methode, um ein HWND\-basierte Hostingumgebung erstellen oder die <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> Methode, um eine WPF\-hosting\-Umgebung zu erstellen. Der zugrunde liegende\-Editor verwendet immer WPF, aber Sie können die Art der Fensterbereich, der Ihrer hostinganforderungen entspricht, wenn Sie diesem Fensterbereich direkt in Ihrer eigenen Inhalte einbetten erstellen.  
  
##### Mithilfe von Win32 und WPF\-Versionen von IVsTextView  
 Sie können festlegen, eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zu Win32 oder WPF\-Modus.  
  
 Wenn eine Editorfactory eine Textansicht standardmäßig erstellt, wird es in ein HWND gehostet, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> Gibt einen HWND zurück. Sie sollten in diesem Modus nicht verwenden, um den Editor in einem WPF\-Steuerelement einzubetten.  
  
 Um eine Textansicht auf WPF\-Modus festzulegen, müssen Sie aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> und übergeben Sie <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> als eines der Initialisierung in kennzeichnet die `InitView` Parameter. Sie erhalten die <xref:System.Windows.FrameworkElement> durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 WPF\-Modus unterscheidet sich von Win32\-Modus auf zwei Arten. Erstens kann die Ansicht für den in einem WPF\-Kontext gehostet werden. Sie können im WPF\-Bereich zugreifen, durch Umwandeln der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> und Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Zweitens <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> weiterhin gibt ein HWND, aber dieses HWND kann nur zum Überprüfen seiner Position und Festlegen des Fokus auf verwendet werden. Sie müssen nicht dieser HWND verwenden Reaktion auf eine WM\_PAINT\-Meldung, da es nicht auswirkt, wie der Editor das Fenster zeichnet. Diese HWND ist nur für den Übergang zu den neuen Editor Code durch den Adapter zu erleichtern. Es wird dringend empfohlen, dass Sie nicht `VIF_NO_HWND_SUPPORT` Wenn die Komponente einen HWND funktioniert, und aufgrund von Beschränkungen im zurückgegebenes HWND erfordert `GetWindowHandle` zwar in diesem Modus.  
  
#### Übergeben von Arrays als Parameter in systemeigenem code  
 Es gibt viele Methoden in der legacy\-API\-Editor, deren Parameter ein Array und die Anzahl enthalten. Beispiele sind:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Wenn Sie diese Methoden in systemeigenem Code aufrufen, müssen Sie jeweils nur ein Element übergeben. Wenn Sie mehr als ein Element übergeben, wird der Anruf aufgrund von Problemen mit der primären Interop\-Implementierung zurückgewiesen.  
  
 Das Problem ist komplexer mit Methoden wie z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Jedes Mal, wenn diese Methode aufgerufen wird, löscht die vorherige Liste der ignorierten Marker\-Typen, daher es nicht möglich ist einfach ist, diese Methode drei Mal mit drei verschiedene Markertypen aufrufen. Die einzige Lösung besteht darin, rufen Sie diese Methode nur in verwaltetem Code.  
  
#### Threading  
 Sie sollten immer den Puffer Adapter vom UI\-Thread aufrufen. Der Puffer\-Adapter ist ein verwaltetes Objekt, d. h., sie aus verwaltetem Code aufrufen, COM\-Marshalling umgehen und der Aufruf automatisch nicht zum Benutzeroberflächenthread gemarshallt werden.  Wenn Sie den Puffer\-Adapter von einem Hintergrundthread aufrufen, können Sie mit <xref:System.Windows.Threading.Dispatcher.Invoke%2A> oder einer ähnlichen Methode.  
  
#### LockBuffer\-Methoden  
 Alle LockBuffer\(\)\-Methoden sind veraltet. Beispiele sind:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### Commit\-Ereignisse  
 Commit\-Ereignisse werden nicht unterstützt. Aufrufen einer Methode, die anweist, für diese Ereignisse bewirkt, dass die Methode einen Fehlercode zurück.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 Die <xref:EnvDTE.TextEditorEvents> auf Commit\(\) nicht mehr ausgelöst werden. Stattdessen werden sie ausgelöst bei jeder Änderung von Text.  
  
#### Text\-Marker  
 Sie müssen Aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Objekte, wenn Sie diese entfernen. In früheren Versionen mussten Sie nur die Marker freigeben.  
  
#### Zeilennummern  
 Für eine Vielzahl von Methoden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, Zeilennummern zugrunde liegenden Puffer Zeilennummern entsprechen, werden keine Zahlen, Faktor bei der Gliederung und Zeilenumbruch, wie in Visual Studio 2008.  
  
 Die betroffenen Methoden gehören \(die Liste ist nicht vollständig\):  
  
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
  
#### Gliedern  
 Clients des <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> sehen nur die Gliederungsbereiche hinzugefügt wurden mit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>oder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Sie werden nicht ad\-hoc\-Regionen angezeigt, da sie nicht über die Editor\-Adapter hinzugefügt werden. Ebenso werden diese Clients nicht angezeigt Gliederungsbereiche Programmiersprachen \(z. B. c\# und C\+\+\), die den neuen Editor Code anstatt die Editor\-Adapter verwenden, hinzugefügt.  
  
#### Höhe der Zeile  
 In der neuen Editor können Textzeilen unterschiedliche Höhen, je nach den Schriftgrad und die möglichen Zeilentransformationen, die die Position relativ zu anderen Positionen verschoben werden können. Die Höhe einer Zeile von Methoden zurückgegeben, wie z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> die Höhe einer Zeile, verwenden die Standardschriftgröße mit keine Zeilentransformationen angewendet wird. Diese Höhe kann oder spiegeln nicht die tatsächliche Höhe einer Zeile in der Ansicht.  
  
#### Ereignisse und rückgängig machen  
 Die Ansicht weiterhin neue Editor für Vorgänge wie das Rendern und Auslösen von Ereignissen kontinuierlich, auch wenn ein Rückgängig\-Cluster geöffnet ist. Dieses Verhalten unterscheidet sich von der älteren Ansichten, die es nicht diese Vorgänge erst nach dem Abschluss des Rückgängig\-Clusters ausgeführt haben.  
  
#### IntelliSense  
  
-   Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Methode schlägt fehl, wenn Sie in einer Klasse übergeben, die nicht entweder implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> oder <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Benutzerdefinierte Win32 Ownerdrawn\-Popups werden nicht mehr unterstützt.  
  
#### SmartTags  
 Adapter können nicht für Smarttags, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> Schnittstellen.  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> ist nicht implementiert.  
  
## Nicht implementierte Methode  
 Einige Methoden wurden nicht auf den Text Puffer Adapter, Text\-Ansicht\-Adapter und Text Ebene Adapter implementiert.  
  
|Schnittstelle|Nicht implementiert|  
|-------------------|-------------------------|  
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
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> wird die Adapter jedoch ignoriert, über die Gliederung Benutzeroberfläche implementiert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> wird die Adapter jedoch ignoriert, über die Gliederung Benutzeroberfläche implementiert.|
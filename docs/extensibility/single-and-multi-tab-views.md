---
title: Einer und mehreren Registerkarten Ansichten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ee4c44cb23c8df5d0a7ea64c54cc37440eaa57c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014977"
---
# <a name="single-and-multi-tab-views"></a>Ansichten mit einer und mehreren Registerkarten
Ein Editor kann verschiedene Arten von Ansichten erstellen. Ein Beispiel ist ein Code-Editor-Fenster, ein weiterer ist ein Forms-Designer.  
  
 Eine Ansicht mit mehreren Registerkarten ist eine Ansicht, die über mehrere Registerkarten verfügt. Der HTML-Editor verfügt beispielsweise über zwei Registerkarten am unteren Rand: **Entwurf** und **Quelle**, die jeweils eine logische Ansicht. Die Entwurfsansicht zeigt einer gerenderten Webseite an, während die andere den HTML-Code zeigt, die die Webseite enthält.  
  
## <a name="accessing-physical-views"></a>Zugriff auf physische Ansichten  
 Physische Ansichten hosten dokumentenansichtsobjekten, jeweils eine Ansicht der Daten in den Puffer, z. B. Code oder eine Form darstellen. Entsprechend hat jede dokumentenansichtsobjekt an eine physische Darstellung (identifiziert durch etwas wie eine Zeichenfolge der physischen Ansicht) und in der Regel eine einzelne logische Ansicht.  
  
 In einigen Fällen jedoch haben eine physische Darstellung zwei oder mehr logische Ansichten. Beispiele sind ein Editor, in dem von einem geteilten Fenster mit Seite-an-Seite-Ansichten oder ein Forms-Designer, der über eine GUI/Entwurfsansicht und eine Ansicht des Code-Behind-der-Formular verfügt.  
  
 Um Ihre-Editor, um Zugriff auf alle verfügbaren physische Ansichten zu aktivieren, müssen Sie eine eindeutige physische Ansicht Zeichenfolge für jeden Typ von dokumentenansichtsobjekt erstellen, die der Editorfactory erstellen können. Z. B. die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Editorfactory kann Dokument Ansichtsobjekte für ein Code-Fenster und ein Forms-Designer-Fenster erstellen.  
  
## <a name="creating-multi-tabbed-views"></a>Erstellen von Ansichten mit mehreren Registerkarten  
 Obwohl eine dokumentenansichtsobjekt eine physische Darstellung über eine eindeutige physische Ansicht Zeichenfolge zugeordnet sein muss, können Sie mehrere Registerkarten, in die physische Ansicht, um die Anzeige von Daten auf unterschiedliche Weise aktivieren platzieren. In dieser Konfiguration mit mehreren Registerkarten alle Registerkarten dieselbe Zeichenfolge, die physische Ansicht zugeordnet sind, aber jede Registerkarte wird eine andere logischen Ansicht GUID zugewiesen.  
  
 Um eine Ansicht mit mehreren Registerkarten für einen Editor erstellen, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> Schnittstelle, und ordnen Sie dann auf eine andere logische Ansicht GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) mit den einzelnen Registerkarten, die Sie erstellen.  
  
 Der Visual Studio-HTML-Editor ist ein Beispiel für einen Editor mit einer Ansicht mehreren Registerkarten. Sie verfügt über **Entwurf** und **Quelle** Registerkarten. Eine andere logische Ansicht bezieht sich auf jeder Registerkarte, um dies zu ermöglichen, `LOGICALVIEWID_TextView` für die **Entwurf** Registerkarte und `LOGICALVIEWID_Code` für die **Quelle** Registerkarte.  
  
 Durch Angabe der entsprechenden logischen Ansicht, kann eine VSPackage die Ansicht zugreifen, die einen bestimmten Zweck, wie ein Formular entwerfen, Bearbeiten von Code oder Debuggen von Code entspricht. Allerdings muss eines der Fenster identifiziert werden, durch die NULL-Zeichenfolge, und dies muss die primäre logischen Ansicht entspricht (`LOGVIEWID_Primary`).  
  
 Die folgende Tabelle enthält die verfügbaren logischen Ansicht Werte und deren Verwendung.  
  
|LOGVIEWID-GUID|Empfohlene Verwendung|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Standardmäßige/primäre Ansicht der Editorfactory.<br /><br /> Alle editorfactorys müssen dieser Wert unterstützt. In dieser Ansicht muss die Zeichenfolge NULL als die Zeichenfolge der physischen Ansicht verwenden. Dieser Wert muss mindestens eine logische Ansicht festgelegt werden.|  
|`LOGVIEWID_Debugging`|Debuggen. In der Regel `LOGVIEWID_Debugging` zugeordnet, die zur gleichen Ansicht wie `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Ansicht gestartet, indem die **Ansichtscode** Befehl.|  
|`LOGVIEWID_Designer`|Ansicht gestartet, indem die **Formular anzeigen** Befehl.|  
|`LOGVIEWID_TextView`|Text-Editor-Ansicht. Dies ist die Ansicht, die zurückgibt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, über die Sie zugreifen können <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Fordert den Benutzer auswählen, welche Ansicht verwenden.|  
|`LOGVIEWID_ProjectSpecificEditor`|Durch Übergeben der **Öffnen mit** im Dialogfeld<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Wenn der Benutzer den Eintrag "(Project Default Editor)" auswählt.|  
  
 Obwohl der logischen Ansichts-GUIDs können erweitert werden, können Sie nur die logische Ansicht GUIDs, die in Ihr VSPackage definiert.  
  
 Beim Herunterfahren behält die Visual Studio die GUID der Editorfactory, die physische Ansicht Zeichenfolgen Dokumentfenster zugeordnet, sodass sie verwendet werden kann, um Dokumentfenster erneut zu öffnen, wenn die Projektmappe erneut geöffnet wird. Nur für Windows, die geöffnet sind, wenn eine Projektmappe geschlossen wird, werden in die Projektmappendatei (SUO) gespeichert. Diese Werte entsprechen den `VSFPROPID_guidEditorType` und `VSFPROPID_pszPhysicalView` übergebenen Werte der `propid` Parameter in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode.  
  
## <a name="example"></a>Beispiel  
 Dieser Codeausschnitt wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> Objekt wird verwendet, um eine Ansicht zugreifen, die implementiert `IVsCodeWindow`. In diesem Fall die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> Dienst dient zum Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> und Anforderung `LOGVIEWID_TextView`, die erhält eines Zeigers auf ein Fensterrahmen. Ein Zeiger auf dem dokumentenansichtsobjekt abgerufen wird, durch den Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> und Angabe des Werts `VSFPROPID_DocView`. Aus dem dokumentenansichtsobjekt `QueryInterface` wird aufgerufen, für die `IVsCodeWindow`. Der Annahme in diesem Fall ist, ein Text-Editor wird zurückgegeben, und daher das dokumentenansichtsobjekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode ist ein Code-Fenster.  
  
```cpp  
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)  
{  
  HRESULT hr;  
  if (NULL == szFile || !*szFile)  
    return E_INVALIDARG;  
  
  if (iLine == -1L)  
    return S_FALSE;  
  
  VSITEMID                  itemid;  
  VARIANT                   var;  
  RECT                      rc;  
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;  
  IVsCodeWindow *           pCodeWin    = NULL;  
  IVsTextView *             pTextView   = NULL;  
  IVsUIHierarchy *          pHierarchy  = NULL;  
  IVsWindowFrame *          pFrame      = NULL;  
  IUnknown *                pUnk        = NULL;  
  IVsHighlight *            pHighlight  = NULL;  
  
  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));  
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));  
  pFrame->Show();  
  VariantInit(&var);  
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));  
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }  
  pUnk = V_UNKNOWN(&var);  
  if (NULL != pUnk)  
  {  
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));  
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||  
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )  
    {  
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);  
      // uncover selection  
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));  
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));  
      UncoverSelectionRect(&rc);  
    }  
  }  
  
Error:  
  CLEARINTERFACE(pHighlight);  
  CLEARINTERFACE(pTextView);  
  CLEARINTERFACE(pCodeWin);  
  CLEARINTERFACE(pUnk);  
  CLEARINTERFACE(pFrame);  
  CLEARINTERFACE(pOpenDoc);  
  CLEARINTERFACE(pHierarchy);  
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);  
  return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Vorgehensweise: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)   
 [Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)
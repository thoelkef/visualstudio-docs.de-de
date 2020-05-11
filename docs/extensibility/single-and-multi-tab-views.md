---
title: Einzel- und Multi-Tab-Ansichten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699989"
---
# <a name="single-and-multi-tab-views"></a>Ansichten mit einer und mehreren Registerkarten
Ein Editor kann verschiedene Arten von Ansichten erstellen. Ein Beispiel ist ein Code-Editor-Fenster, ein anderes ist ein Formular-Designer.

 Eine Ansicht mit mehreren Registerkarten ist eine Ansicht mit mehreren Registerkarten. Der HTML-Editor verfügt beispielsweise über zwei Registerkarten am unteren Rand: **Design** und **Quelle**, jede eine logische Ansicht. In der Entwurfsansicht wird eine gerenderte Webseite angezeigt, während auf der anderen Seite der HTML-Code angezeigt wird, der die Webseite umfasst.

## <a name="accessing-physical-views"></a>Zugriff auf physische Ansichten
 Physische Ansichten hosten Dokumentansichtsobjekte, die jeweils eine Ansicht von Daten im Puffer darstellen, z. B. Code oder ein Formular. Dementsprechend verfügt jedes Dokumentansichtsobjekt über eine physische Ansicht (identifiziert durch eine als physische Ansichtszeichenfolge bezeichnete Ansichtszeichenfolge) und im Allgemeinen über eine einzelne logische Ansicht.

 In einigen Fällen kann eine physische Ansicht jedoch zwei oder mehr logische Ansichten haben. Einige Beispiele sind ein Editor mit einem geteilten Fenster mit nebeneinander-Ansichten oder ein Formular-Designer mit gui/design-Ansicht und einer Code-behind-the-Form-Ansicht.

 Damit der Editor auf alle verfügbaren physischen Ansichten zugreifen kann, müssen Sie für jeden Dokumentansichtsobjekttyp, den die Editor factory erstellen kann, eine eindeutige physische Ansichtszeichenfolge erstellen. Die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Editorfactory kann z. B. Dokumentansichtsobjekte für ein Codefenster und ein Formular-Designerfenster erstellen.

## <a name="creating-multi-tabbed-views"></a>Erstellen von Ansichten mit mehreren Tabbetten
 Obwohl ein Dokumentansichtsobjekt einer physischen Ansicht über eine eindeutige physische Ansichtszeichenfolge zugeordnet werden muss, können Sie mehrere Registerkarten in der physischen Ansicht platzieren, um die Anzeige von Daten auf unterschiedliche Weise zu ermöglichen. In dieser Konfiguration mit mehreren Registerkarten sind alle Registerkarten derselben physischen Ansichtszeichenfolge zugeordnet, aber jede Registerkarte erhält eine andere GUID für logische Ansicht.

 Um eine Ansicht mit mehreren Registerkarten für <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> einen Editor zu erstellen, implementieren<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>Sie die Schnittstelle, und ordnen Sie dann jeder registerkarte, die Sie erstellen, eine andere guiD ( ) für die logische Ansicht zu.

 Der Visual Studio-HTML-Editor ist ein Beispiel für einen Editor mit einer Ansicht mit mehreren Registerkarten. Es verfügt über **Design-** und Quell-Registerkarten. **Source** Um dies zu aktivieren, ist jeder `LOGICALVIEWID_TextView` Registerkarte, für `LOGICALVIEWID_Code` die Registerkarte **Entwurf** und für die Registerkarte **Quelle** eine andere logische Ansicht zugeordnet.

 Durch Die Angabe der entsprechenden logischen Ansicht kann ein VSPackage auf die Ansicht zugreifen, die einem bestimmten Zweck entspricht, z. B. das Entwerfen eines Formulars, das Bearbeiten von Code oder das Debuggen von Code. Eines der Fenster muss jedoch durch die NULL-Zeichenfolge identifiziert werden,`LOGVIEWID_Primary`und dies muss der primären logischen Ansicht ( ) entsprechen.

 In der folgenden Tabelle sind die verfügbaren logischen Ansichtswerte und deren Verwendung aufgeführt.

|LOGVIEWID-GUID|Empfohlene Verwendung|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Standard-/Primäransicht der Editorfactory.<br /><br /> Alle Editor-Fabriken müssen diesen Wert unterstützen. Diese Ansicht muss die NULL-Zeichenfolge als physische Ansichtszeichenfolge verwenden. Mindestens eine logische Ansicht muss auf diesen Wert festgelegt werden.|
|`LOGVIEWID_Debugging`|Debuggen der Ansicht. In `LOGVIEWID_Debugging` der Regel wird `LOGVIEWID_Code`derselben Ansicht wie zugeordnet.|
|`LOGVIEWID_Code`|Ansicht, die mit dem Befehl **Code anzeigen** gestartet wird.|
|`LOGVIEWID_Designer`|Ansicht, die mit dem Befehl **Formular anzeigen** gestartet wird.|
|`LOGVIEWID_TextView`|Texteditor-Ansicht. Dies ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>Ansicht, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>zurückgibt, aus der Sie zugreifen können.|
|`LOGVIEWID_UserChooseView`|Fordert den Benutzer auf, auszuwählen, welche Ansicht verwendet werden soll.|
|`LOGVIEWID_ProjectSpecificEditor`|Durch das Dialogfeld **Öffnen mit** übergeben, um<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> wenn der Benutzer den Eintrag "(Project default editor)" auswählt.|

 Obwohl logische Ansichts-GUIDs erweiterbar sind, können Sie nur die in Ihrem VSPackage definierten GUIDs für logische Ansicht verwenden.

 Beim Herunterfahren behält Visual Studio die GUID der Editorfactory und die dem Dokumentfenster zugeordneten physischen Ansichtszeichenfolgen bei, sodass es zum erneuten Öffnen von Dokumentfenstern verwendet werden kann, wenn die Projektmappe erneut geöffnet wird. Nur Fenster, die geöffnet sind, wenn eine Lösung geschlossen wird, werden in der Lösungsdatei (.suo) beibehalten. Diese Werte entsprechen `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` den und `propid` Werten, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> die im Parameter in der Methode übergeben werden.

## <a name="example"></a>Beispiel
 Dieser Ausschnitt veranschaulicht, wie <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> das Objekt für den Zugriff `IVsCodeWindow`auf eine Ansicht verwendet wird, die implementiert. In diesem Fall <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> wird der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Dienst `LOGVIEWID_TextView`zum Aufrufen und Anfordern verwendet, das einen Zeiger auf einen Fensterrahmen abruft. Ein Zeiger auf das Dokumentansichtsobjekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> wird abgerufen, `VSFPROPID_DocView`indem ein Wert von aufgerufen und angegeben wird. Aus dem Dokumentansichtsobjekt `QueryInterface` `IVsCodeWindow`wird für aufgerufen. In diesem Fall wird erwartet, dass ein Texteditor zurückgegeben wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> sodass das in der Methode zurückgegebene Dokumentansichtsobjekt ein Codefenster ist.

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

## <a name="see-also"></a>Weitere Informationen
- [Unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)
- [Gewusst wie: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)
- [Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)

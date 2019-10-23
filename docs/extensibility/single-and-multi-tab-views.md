---
title: Ansichten für einzelne und mehrere Registerkarten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c651bda042524b2ed3188fef880f848bb0087433
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720062"
---
# <a name="single-and-multi-tab-views"></a>Ansichten mit einer und mehreren Registerkarten
Ein Editor kann verschiedene Typen von Ansichten erstellen. Ein Beispiel hierfür ist ein Code-Editor-Fenster, ein weiteres ist ein Forms-Designer.

 Eine Ansicht mit mehreren Registerkarten ist eine Ansicht mit mehreren Registerkarten. Der HTML-Editor verfügt beispielsweise über zwei Registerkarten am unteren Rand: **Entwurf** und **Quelle**, jeweils eine logische Ansicht. In der Entwurfs Ansicht wird eine gerenderte Webseite angezeigt, während die andere den HTML-Code anzeigt, der die Webseite umfasst.

## <a name="accessing-physical-views"></a>Zugreifen auf physische Sichten
 Physische Sichten hosten Dokument Ansichts Objekte, die jeweils eine Ansicht der Daten im Puffer darstellen (z. b. Code oder ein Formular). Dementsprechend hat jedes Dokument Ansichts Objekt eine physische Ansicht (identifiziert durch etwas, das als physische Ansichts Zeichenfolge bezeichnet wird) und in der Regel eine einzelne logische Ansicht.

 In einigen Fällen kann eine physische Ansicht jedoch über zwei oder mehr logische Sichten verfügen. Bei einigen Beispielen handelt es sich um einen Editor, der über ein geteiltes Fenster mit parallelen Ansichten verfügt, oder um einen Formular-Designer, der über eine GUI/Entwurfs Ansicht und eine Code-Behind-the-Form-Ansicht verfügt.

 Damit der Editor auf alle verfügbaren physischen Ansichten zugreifen kann, müssen Sie für jeden Typ von Dokument Ansichts Objekt, das die Editorfactory erstellen kann, eine eindeutige physische Ansichts Zeichenfolge erstellen. Beispielsweise kann die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Editor-Factory Dokument Ansichts Objekte für ein Code Fenster und ein Formular-Designer-Fenster erstellen.

## <a name="creating-multi-tabbed-views"></a>Erstellen von Ansichten mit mehreren Registerkarten
 Obwohl ein Dokument Ansichts Objekt einer physischen Ansicht über eine eindeutige physische Ansichts Zeichenfolge zugeordnet werden muss, können Sie mehrere Registerkarten innerhalb der physischen Ansicht platzieren, um die Anzeige von Daten auf verschiedene Weise zu ermöglichen. Bei dieser Konfiguration mit mehreren Registerkarten werden alle Registerkarten derselben physischen Ansichts Zeichenfolge zugeordnet, aber jeder Registerkarte wird eine andere logische Ansichts-GUID zugewiesen.

 Um für einen Editor eine Ansicht mit mehreren Registerkarten zu erstellen, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>-Schnittstelle implementieren und dann jeder von Ihnen erstellten Registerkarte eine andere logische Ansichts-GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) zuordnen.

 Der HTML-Editor von Visual Studio ist ein Beispiel für einen Editor mit einer Ansicht mit mehreren Registerkarten. Es verfügt über **Entwurfs** -und **Quell** Registerkarten. Um dies zu ermöglichen, wird jeder Registerkarte eine andere logische Ansicht zugeordnet, `LOGICALVIEWID_TextView` für die Registerkarte **Entwurf** und `LOGICALVIEWID_Code` für die Registerkarte **Quelle** .

 Durch die Angabe der entsprechenden logischen Ansicht kann ein VSPackage auf die Sicht zugreifen, die einem bestimmten Zweck entspricht, z. b. das Entwerfen eines Formulars, das Bearbeiten von Code oder das Debuggen von Code. Eines der Fenster muss jedoch durch die NULL-Zeichenfolge identifiziert werden, und diese muss der primären logischen Ansicht (`LOGVIEWID_Primary`) entsprechen.

 In der folgenden Tabelle sind die verfügbaren logischen Ansichts Werte und deren Verwendung aufgeführt.

|logviewid-GUID|Empfohlene Verwendung|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Standard/primäre Ansicht der Editorfactory.<br /><br /> Alle editorfactorys müssen diesen Wert unterstützen. In dieser Sicht muss die NULL-Zeichenfolge als physische Ansichts Zeichenfolge verwendet werden. Mindestens eine logische Ansicht muss auf diesen Wert festgelegt werden.|
|`LOGVIEWID_Debugging`|Debugansicht. In der Regel wird `LOGVIEWID_Debugging` der gleichen Ansicht wie `LOGVIEWID_Code` zugeordnet.|
|`LOGVIEWID_Code`|Ansicht, die vom Befehl " **Code anzeigen** " gestartet wird.|
|`LOGVIEWID_Designer`|Ansicht, die vom Befehl " **Formular anzeigen** " gestartet wird.|
|`LOGVIEWID_TextView`|Text-Editor-Ansicht. Dies ist die Ansicht, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> zurückgibt, von dem aus Sie auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zugreifen können.|
|`LOGVIEWID_UserChooseView`|Fordert den Benutzer auf, die zu verwendende Ansicht auszuwählen.|
|`LOGVIEWID_ProjectSpecificEditor`|Wird vom Dialogfeld **Öffnen mit** an<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Wenn der Benutzer den Eintrag "(Projekt Standard-Editor)" auswählt.|

 Obwohl die GUIDs der logischen Ansicht erweiterbar sind, können Sie nur die in Ihrem VSPackage definierten GUIDs der logischen Ansicht verwenden.

 Beim Herunterfahren behält Visual Studio die GUID der Editorfactory und die dem Dokument Fenster zugeordneten physischen Ansichts Zeichenfolgen bei, damit Sie Dokument Fenster erneut öffnen kann, wenn die Projekt Mappe erneut geöffnet wird. Nur Fenster, die geöffnet sind, wenn eine Projekt Mappe geschlossen wird, werden in der Projektmappendatei (. suo) beibehalten. Diese Werte entsprechen den `VSFPROPID_guidEditorType`-und `VSFPROPID_pszPhysicalView` Werten, die in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>-Methode im `propid`-Parameter übergeben werden.

## <a name="example"></a>Beispiel
 Dieser Code Ausschnitt veranschaulicht, wie das <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> Objekt verwendet wird, um auf eine Ansicht zuzugreifen, die `IVsCodeWindow` implementiert. In diesem Fall wird der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>-Dienst verwendet, um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> aufzurufen und `LOGVIEWID_TextView` anzufordern, der einen Zeiger auf einen Fensterrahmen erhält. Ein Zeiger auf das Dokument Ansichts Objekt wird abgerufen, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> aufgerufen und der Wert `VSFPROPID_DocView` angegeben wird. Aus dem Dokument Ansichts Objekt wird `QueryInterface` für `IVsCodeWindow` aufgerufen. In diesem Fall wird erwartet, dass ein Text-Editor zurückgegeben wird, sodass das in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>-Methode zurückgegebene Dokument Ansichts Objekt ein Code Fenster ist.

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
- [Unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)
- [Gewusst wie: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)
- [Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)
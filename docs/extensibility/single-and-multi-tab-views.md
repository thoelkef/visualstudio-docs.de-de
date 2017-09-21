---
title: "Einzelne und mehrere Registerkarte Ansichten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] benutzerdefinierte - Ansichten für einzelne und mehrere Registerkarte"
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Einzelne und mehrere Registerkarte Ansichten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Editor können verschiedene Typen von Ansichten erstellen.  Ein Beispiel hierfür ist ein Code\-Editor\-Fenster, ist ein anderes Formular\-Designer.  
  
 Eine Ansicht MULTI\-im Registerkartenformat ist eine Ansicht, die mehrere Registerkarten verfügt.  Beispielsweise verfügt der HTML\-Editor folgenden zwei Registerkarten: **Entwurf** und **Quelle**, die jeweils eine logische Ansicht.  Die Entwurfsansicht zeigt eine gerenderte Webseite an, während die andere den HTML\-Code anzuzeigen, das die Webseite enthält.  
  
## Zugreifen auf Systemtest\-Ansichten  
 physikalischen Host wird dokumenten\-Ansichts Objekte, die jeweils mit einer Ansicht von Daten im Puffer, wie Code oder in einem Formular darstellt.  Dementsprechend verfügt jedes Objekt eine physikalische Ansicht der Dokumente, identifiziert durch \(bezeichnet als eine Zeichenfolge der Ansicht eine physikalische\) und im Allgemeinen eine einzelne logische Ansicht.  
  
 In einigen Fällen jedoch eine physikalische Sicht verfügen oder zwei Ansichten logischere kann.  Einige Beispiele sind ein Editor, in dem ein geteiltes Fenster Parallele Ansichten verfügt, oder mit einem Formular\-Designer, der eine GUI\-\/design und eine Code\-hinter\-d Formular Sicht hat.  
  
 Um den Editor zu aktivieren, um alle verfügbaren physischen Ansichten zuzugreifen, müssen Sie eine eindeutige Zeichenfolge der Ansicht physische für jeden Typ von Dokumenten für den Erstellen der Editor die factory erstellen kann.  Beispielsweise kann die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Editor Dokumente factory die Objekte für ein Codefenster, und ein Fenster Formular\-Designer erstellen.  
  
## Erstellen von Ansichten MULTI\-Im Registerkartenformat  
 Obwohl die Dokumente ein Objekt in einer physischen Ansicht anzeigen physische durch eine eindeutige Zeichenfolge zugeordnet werden muss, können Sie mehrere Registerkarten in der physischen Ansicht ablegen, um das Anzeigen von Daten auf unterschiedliche Weise zu aktivieren.  In dieser Konfiguration MULTI\-im Registerkartenformat werden alle Registerkarten mit derselben physikalischen Zeichenfolge Ansicht zugeordnet, aber jede Registerkarte ist eine weitere logische Ansicht GUID angegeben.  
  
 Um eine Ansicht MULTI\-im Registerkartenformat für einen Editor zu erstellen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView>\-Schnittstelle, und ordnen Sie dann eine weitere logische Ansicht \(GUID\)<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>mit jeder Registerkarte, die Sie erstellen.  
  
 Der Visual Studio\-HTML\-Editor ist ein Beispiel für einen Editor mit einer Umgebung mit mehreren Registerkarte Ansicht.  Sie verfügt über **Entwurf** und **Quelle** Tabstopps.  Dazu wird eine weitere logische Ansicht mit jeder Registerkarte, `LOGICALVIEWID_TextView` für die **Entwurf** Registerkarte, und `LOGICALVIEWID_Code` für die **Quelle** Registerkarte zugeordnet.  
  
 Mit den entsprechenden logische Ansicht angibt, kann ein VSPackage die Ansicht zugreifen, die zu einem bestimmten Zweck, wie Entwerfen eines Formulars entspricht und Code oder Debugcode bearbeitet.  Allerdings muss eines der Fenster durch die NULL\-Zeichenfolge identifiziert und es muss`LOGVIEWID_Primary`logischen Primärschlüssel \(Sicht\) entsprechen.  
  
 In der folgenden Tabelle sind die verfügbaren logischen Werte anzeigen und ihre Verwendung.  
  
|LOGVIEWID GUID|Empfohlene Verwendung|  
|--------------------|---------------------------|  
|`LOGVIEWID_Primary`|Standardwert\/primäre Ansicht der Editor factorys.<br /><br /> Alle Editorfactorys müssen diesen Wert unterstützen.  Diese Sicht muss die NULL\-Zeichenfolge verwenden z. B. seine physische Zeichenfolge der Ansicht.  muss mindestens eine logische Ansicht auf diesen Wert festgelegt werden.|  
|`LOGVIEWID_Debugging`|Ansicht debuggen.  In der Regel wird `LOGVIEWID_Debugging` wie bei den zugeordnet `LOGVIEWID_Code`an.|  
|`LOGVIEWID_Code`|Ansicht, die vom **Code anzeigen** Befehl.|  
|`LOGVIEWID_Designer`|Ansicht, die vom **Formular anzeigen** Befehl.|  
|`LOGVIEWID_TextView`|Text\-Editor\-Ansicht.  Dies ist die Ansicht, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>zurückgibt, von denen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>zugreifen können.|  
|`LOGVIEWID_UserChooseView`|Fordert den Benutzer auf, denen auszuwählen.|  
|`LOGVIEWID_ProjectSpecificEditor`|Werden vom **Öffnen mit** Dialogfeld zu<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> \(„wenn der Benutzer mit dem Standard\-Editor Eintrag“ des Projekts\) auswählt.|  
  
 Obwohl logische Ansicht GUID erweiterbar sind, können Sie nur die logische Sicht GUIDs verwenden, die in einem VSPackage definiert ist.  
  
 Klicken Sie auf Herunterfahren Visual Studio behält die GUID der Editor anzeigen und der physischen factorys Formatzeichenfolgen bei, die mit dem Dokumentfenster zugeordnet werden, damit er verwendet werden kann, um Dokumentfenster erneut zu öffnen, wenn die Projektmappe erneut geöffnet wird.  Nur Windows, die geöffnet werden, wenn eine Projektmappe geschlossen ist, werden in der Projektmappendatei \(.suo\) beibehalten.  Diese Werte entsprechen den `VSFPROPID_guidEditorType` und `VSFPROPID_pszPhysicalView`\-Werten, die in den `propid`\-Parameter in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>\-Methode übergeben werden.  
  
## Beispiel  
 Dieser Codeausschnitt wird veranschaulicht, wie das <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView>\-Objekt verwendet wird, um eine Ansicht zugreifen, die `IVsCodeWindow`implementiert.  In diesem Fall wird der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> Dienst verwendet, um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> aufzurufen und `LOGVIEWID_TextView`anzufordern, der ein Zeiger auf einen Fensterrahmen abgerufen wird.  Ein Zeiger auf den Dokumenten für die wird abgerufen, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> aufrufen und einen Wert von `VSFPROPID_DocView`angibt.  Wählen Sie die Dokumente Objekt wird `QueryInterface` für `IVsCodeWindow`aufgerufen.  Die Annahme ist in diesem Fall, dass ein Text\-Editor zurückgegeben wird, und deshalb ist das Objekt, das die Dokumente in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>\-Methode zurückgegebene ein Codefenster.  
  
```cpp#  
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
  
## Siehe auch  
 [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Gewusst wie: Anfügen von Ansichten, um Daten](../extensibility/how-to-attach-views-to-document-data.md)   
 [Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)
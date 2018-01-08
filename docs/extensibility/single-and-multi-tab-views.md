---
title: "Ansichten für einzelne und Registerkarte \"Multi\" | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f20e5d251d8d6ef31289fb1b9ee8b9420ff9146a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="single-and-multi-tab-views"></a>Ansichten für einzelne und Registerkarte "Multi"
Erstellen eines Editors kann verschiedene Arten von Ansichten. Ein Beispiel ist ein Code-Editor-Fenster, ein weiterer Vorteil ist ein Forms-Designer.  
  
 Eine Registerkarten-Ansicht ist eine Sicht, die mehrere Registerkarten verfügt. Z. B. der HTML-Editor verfügt über zwei Registerkarten am unteren: **Entwurf** und **Quelle**, die jeweils eine logische Sicht. Die Entwurfsansicht zeigt einer gerenderten Webseite an, während die andere den HTML-Code zeigt, die auf der Webseite besteht aus.  
  
## <a name="accessing-physical-views"></a>Beim Zugriff auf physische Ansichten  
 Physische Ansichten Hostobjekte Dokument anzeigen, jeweils eine Ansicht der Daten in den Puffer, z. B. Code oder eine Form darstellen. Dementsprechend ist jede dokumentansichtsobjekts eine physische Ansicht (identifiziert etwas anderes als eine Zeichenfolge für die physische Ansicht bezeichnet) und in der Regel eine einzelne logische Sicht.  
  
 In einigen Fällen kann eine physische Ansicht jedoch mindestens zwei logische Ansichten haben. Beispiele hierfür sind einen Editor, der einem geteilten Fenster mit Ansichten Seite-an-Seite verfügt oder ein Forms-Designer, der eine GUI/Entwurfsansicht und eine Code-Behind-des-Formulars Ansicht verfügt.  
  
 Um den Zugriff auf alle verfügbaren physischen Ansichten Editor zu aktivieren, müssen Sie eine eindeutige physische Ansicht Zeichenfolge für jeden Typ von dokumentansichtsobjekts erstellen, die der Editorfactory erstellen können. Z. B. die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] -Editor-Factory kann Dokument Sichtobjekte für ein Codefenster und ein Forms-Designer-Fenster erstellen.  
  
## <a name="creating-multi-tabbed-views"></a>Erstellen von Ansichten mit mehreren Registerkarten  
 Obwohl ein Document-Objekt für eine physische Ansicht über eine eindeutige physische Ansicht Zeichenfolge zugeordnet werden soll, muss, können Sie mehrere Registerkarten innerhalb der physischen Ansicht so aktivieren Sie die Anzeige von Daten auf unterschiedliche Weise platzieren. In dieser Konfiguration Registerkarten alle Registerkarten sind die gleiche physische Ansicht Zeichenfolge zugeordnet, aber jede Registerkarte wird eine andere logische Ansicht GUID zugewiesen.  
  
 Um eine Sicht Registerkarten für einen Editor erstellen, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> Schnittstelle, und ordnen Sie eine andere logischen Ansicht GUID (<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>) mit den einzelnen Registerkarten, die Sie erstellen.  
  
 Visual Studio-HTML-Editor ist ein Beispiel für einen Editor mit einer Ansicht der Registerkarte "Multi". Es wurde **Entwurf** und **Quelle** Registerkarten. Um dies zu ermöglichen, eine andere logische Ansicht bezieht sich auf jeder Registerkarte `LOGICALVIEWID_TextView` für die **Entwurf** Registerkarte und `LOGICALVIEWID_Code` für die **Quelle** Registerkarte.  
  
 Durch die Angabe der entsprechenden logischen Ansicht, kann eine VSPackage die Ansicht zugreifen, die einen bestimmten Zweck, z. B. ein Formular entwerfen, Bearbeiten von Code oder Debugcode entspricht. Allerdings muss eines der Fenster identifiziert werden, durch die NULL-Zeichenfolge und dadurch die primäre logische Sicht entsprechen (`LOGVIEWID_Primary`).  
  
 Die folgende Tabelle enthält die verfügbaren logischen Ansicht Werte und deren Verwendung.  
  
|LOGVIEWID-GUID|Empfohlene Verwendung|  
|--------------------|---------------------|  
|`LOGVIEWID_Primary`|Standard/primäre Server Überblick über die Editor-Factory.<br /><br /> Dieser Wert müssen alle editorfactorys unterstützt werden. In dieser Ansicht muss die NULL-Zeichenfolge als die physische Ansicht Zeichenfolge verwenden. Mit diesem Wert muss mindestens eine logische Sicht festgelegt werden.|  
|`LOGVIEWID_Debugging`|Debuggen die Ansicht. In der Regel `LOGVIEWID_Debugging` ordnet die gleiche Ansicht als `LOGVIEWID_Code`.|  
|`LOGVIEWID_Code`|Ansicht gestartet, indem Sie die **Code anzeigen** Befehl.|  
|`LOGVIEWID_Designer`|Ansicht gestartet, indem Sie die **Formular anzeigen** Befehl.|  
|`LOGVIEWID_TextView`|Text-Editor-Ansicht. Dies ist die Ansicht, die zurückgibt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>, aus denen Sie Zugriff haben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|`LOGVIEWID_UserChooseView`|Fordert den Benutzer auswählen, welche Ansicht verwenden.|  
|`LOGVIEWID_ProjectSpecificEditor`|Durch Übergeben der **Öffnen mit** im Dialogfeld<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Wenn der Benutzer den Eintrag "(Projekt Standard-Editor)" auswählt.|  
  
 Obwohl die logische Sicht GUIDs sind erweiterbar, können Sie nur die logische Sicht GUIDs, die in Ihr VSPackage definiert.  
  
 Beim Herunterfahren behält Visual Studio die GUID des die Editor-Factory und die physische Ansicht-Zeichenfolgen, die verknüpft sind mit dem Dokumentfenster, damit es verwendet werden kann, um Dokumentfenster erneut zu öffnen, wenn die Projektmappe erneut geöffnet wird. Nur Windows, die geöffnet sind, wenn eine Projektmappe geschlossen wird, werden in der Projektmappendatei (SUO) beibehalten. Diese Werte entsprechen den `VSFPROPID_guidEditorType` und `VSFPROPID_pszPhysicalView` übergebenen Werte der `propid` Parameter in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode.  
  
## <a name="example"></a>Beispiel  
 Dieser Codeausschnitt wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> Objekt wird verwendet, um den Zugriff auf eine Sicht, die implementiert `IVsCodeWindow`. In diesem Fall die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> Inanspruchnahme Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> und Anforderung `LOGVIEWID_TextView`, dem einen Zeiger auf einen Fensterrahmen abruft. Ein Zeiger auf das Ansichtsobjekt Dokument abgerufen wird, durch den Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> und dabei den Wert `VSFPROPID_DocView`. Aus der dokumentansichtsobjekts `QueryInterface` heißt für `IVsCodeWindow`. In diesem Fall wird erwartet, dass in ein Text-Editor wird zurückgegeben, und daher des dokumentansichtsobjekts die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode ist ein Codefenster.  
  
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
 [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Vorgehensweise: Anfügen von Ansichten, um Daten zu dokumentieren.](../extensibility/how-to-attach-views-to-document-data.md)   
 [Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)
---
title: "Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88f7d2bf3a3351999175425366cf421c3b5ce0b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-file-change-notifications"></a>Vorgehensweise: Dateiänderungsbenachrichtigungen unterdrücken
Wenn die physische Datei, die den Textpuffer darstellt geändert wurde, wird ein Dialogfeld angezeigt, mit der Meldung **möchten Sie die Änderungen auf die folgenden Elemente zu speichern?** Dies wird als Datei-änderungsbenachrichtigung bezeichnet. Wenn viele Änderungen in der Datei werden möchten, kann jedoch dieses Dialogfeld anzeigen immer wieder schnell lästig werden.  
  
 Sie können das Dialogfeld zu öffnen, die mit dem folgenden Verfahren programmgesteuert unterdrücken. Auf diese Weise können Sie eine Datei sofort laden, ohne den Benutzer auffordern, die Änderungen jedes Mal zu speichern.  
  
### <a name="to-suppress-file-change-notification"></a>Datei-änderungsbenachrichtigung unterdrücken  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode, um zu bestimmen, welche TextBuffer-Objekt der geöffneten Datei zugeordnet ist.  
  
2.  Direkte der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> -Objekt, das im Arbeitsspeicher, um ignorieren dateiänderungen, durch Abrufen überwacht wird der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> -Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (Dokumentdaten)-Objekt, und implementieren Sie dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> Methode mit der `fIgnore` Parameter Legen Sie auf `true`.  
  
3.  Rufen Sie die Methoden auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstellen, die im Arbeitsspeicher aktualisiert <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt mit den Änderungen der Datenbankdatei (z. B. wenn ein Feld für Ihre Komponente hinzugefügt wird).  
  
4.  Aktualisieren Sie die Datei auf dem Datenträger mit den Änderungen, unabhängig von der alle ausstehenden Änderungen, die der Benutzer möglicherweise ausgeführt haben.  
  
     Auf diese Weise, wenn Sie leiten die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> änderungsbenachrichtigungen für Objekt, das Fortsetzen der Überwachung für die Datei, die der Textpuffer im Arbeitsspeicher Version stellt die Änderungen, die Sie generiert haben, sowie alle anderen ausstehenden Änderungen. Die Datei auf Datenträger reflektiert den aktuellen Code, der von Ihnen erstellte, und alle gespeicherten Änderungen vom Benutzer zuvor im Code Benutzer bearbeitet.  
  
5.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> Methode zum Benachrichtigen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt zum Fortsetzen der Überwachung für dateiänderungsbenachrichtigungen durch Festlegen der `fIgnore` Parameter `false`.  
  
6.  Wenn Sie beabsichtigen, mehrere Änderungen in der Datei, wie im Fall von Quellcodeverwaltungssystem (SCC), müssen Sie globale Änderung Dateidienst dateiänderungsbenachrichtigungen vorübergehend anhalten mitteilen.  
  
     Z. B. Wenn Sie die Datei schreiben und ändern Sie den Zeitstempel, müssen Sie die dateiänderungsbenachrichtigungen angehalten wird, wie die neue Version und Timestample Vorgänge jedes, zählen als eine separate Datei Änderungsereignis. Um die globalen Datei-änderungsbenachrichtigung zu aktivieren, Sie stattdessen rufen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Datei-änderungsbenachrichtigung zu unterdrücken.  
  
```cpp  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn umfasst mehrere Änderungen an der Datei, wie im Fall von SCC, die Ihren Fall ist es wichtig, globale dateiänderungsbenachrichtigungen vor einer Warnung die Dokumentdaten zum Fortsetzen der Überwachung für dateiänderungen fortgesetzt.
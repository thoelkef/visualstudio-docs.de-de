---
title: 'Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 108910c52033af3574a004cf314be2628fd54122
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955477"
---
# <a name="how-to-suppress-file-change-notifications"></a>Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn die physische Datei, die den Textpuffer darstellt geändert wurde, wird ein Dialogfeld anzeigt, mit der Meldung **möchten Sie die folgenden Elemente speichern?** Dies wird als dateiänderungsbenachrichtigung bezeichnet. Wenn viele Änderungen in der Datei werden möchten, kann jedoch dieses Dialogfeld können Sie immer wieder anzeigen schnell lästig werden.  
  
 Sie können dieses Dialogfeld können Sie mit dem folgenden Verfahren programmgesteuert unterdrücken. Auf diese Weise können Sie eine Datei direkt erneut laden ohne den Benutzer auffordern, die Änderungen jedes Mal zu speichern.  
  
### <a name="to-suppress-file-change-notification"></a>Dateiänderungsbenachrichtigung unterdrückt werden sollen.  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode, um zu bestimmen, welche TextBuffer-Objekt der geöffneten Datei zugeordnet ist.  
  
2.  Direkte der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> -Objekt, das im Arbeitsspeicher, um das ignorieren dateiänderungen durch Abrufen überwacht der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> -Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (Dokumentdaten)-Objekt, und ein anschließendes Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> -Methode mit der `fIgnore` Parameter Legen Sie auf `true`.  
  
3.  Rufen Sie die Methoden auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstellen, die im Arbeitsspeicher aktualisiert <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt mit den Änderungen der Datenbankdatei (z. B. wenn ein Feld für Ihre Komponente hinzugefügt wird).  
  
4.  Aktualisieren Sie die Datei auf dem Datenträger mit den Änderungen, ohne Sie in Betracht ziehen, alle ausstehenden Änderungen, die der Benutzer möglicherweise ausgeführt haben.  
  
     Auf diese Weise, wenn Sie leiten die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> änderungsbenachrichtigungen für Objekt, das Fortsetzen der Überwachung für die Datei, das den Textpuffer im Arbeitsspeicher die Änderungen, die Sie generiert haben, sowie alle anderen ausstehenden Änderungen wider. Datei auf dem Datenträger Gibt den aktuellen Code, der von Ihnen generierte, und alle Änderungen, die vom Benutzer zuvor im Code bearbeitet werden, Benutzer gespeichert.  
  
5.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> -Methode benachrichtigt die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt, das Fortsetzen der Überwachung für dateiänderungsbenachrichtigungen durch Festlegen der `fIgnore` Parameter, um `false`.  
  
6.  Wenn Sie mehrere Änderungen an der Datei, wie im Fall von quellcodeverwaltung (SCC), vornehmen möchten, müssen Sie die globale dateiänderungsdienst dateiänderungsbenachrichtigungen zeitweise zu unterbrechen mitteilen.  
  
     Z. B. Wenn Sie die Datei schreiben und ändern Sie dann auf den Zeitstempel, müssen Sie die dateiänderungsbenachrichtigungen, anhalten, die Operationen schreiben und Timestample jeweils berücksichtigt, wie eine separate Datei Änderungsereignis. Um die globale dateiänderungsbenachrichtigung zu aktivieren, Sie stattdessen rufen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht, wie dateiänderungsbenachrichtigung unterdrückt werden sollen.  
  
```cpp#  
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
 Wenn umfasst mehrere Änderungen an der Datei, wie im Fall von SCC, das Ihrem Fall ist es wichtig, globale dateiänderungsbenachrichtigungen Warnungen die Dokumentendaten zum Fortsetzen der Überwachung für dateiänderungen fortsetzen.

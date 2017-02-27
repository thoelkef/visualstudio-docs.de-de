---
title: "Gewusst wie: Unterdr&#252;cken von Datei&#228;nderungsbenachrichtigungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - unterdrücken Datei"
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Gewusst wie: Unterdr&#252;cken von Datei&#228;nderungsbenachrichtigungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn die physische Datei, die den Textpuffer darstellt, geändert wurde, Anzeigen eines Dialogfelds mit der Nachricht **Möchten Sie die Änderungen für die folgenden Elemente speichern?** Dies wird als Datei änderungsbenachrichtigung.  Wenn viele Änderungen an der Datei sein werden, das dieses Dialogfelds kann jedoch immer wieder angezeigt werden, schnell ärgerlich sein.  
  
 Sie können dieses Dialogfeld mithilfe der folgenden Verfahren programmgesteuert unterdrücken.  Auf diese Weise können Sie eine Datei sofort neu laden, ohne den Benutzer aufzufordern, die jedes Mal Änderungen zu speichern.  
  
### So unterdrücken änderungsbenachrichtigung Datei  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>\-Methode auf, um zu bestimmen, welche Puffer Objekt zugeordnete Datei öffnen wird simsen.  
  
2.  Verweisen auf das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\-Objekt, das im Arbeitsspeicher ist, die Datei Überwachen von Änderungen zu ignorieren, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>\-Schnittstelle des Objekts <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> \(Dokumentdaten\) abruft, und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>\-Methode mit dem `fIgnore`\-Parameter zu implementieren, der dann `true`festgelegt ist.  
  
3.  Rufen Sie die Methoden für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>\-Schnittstellen an, um das Objekt im Arbeitsspeicher <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> mit der Dateiänderungen \(z. B. zu aktualisieren, wenn ein Feld an die Komponente hinzugefügt wird\).  
  
4.  Aktualisieren Sie die Datei auf dem Datenträger mit den Änderungen, ohne alle anstehenden Bearbeitungen zu beachten, die der Benutzer möglicherweise laufendes verfügt.  
  
     Auf diese Weise wenn Sie das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\-Objekt der abstrakten überwachung für die Datei änderungsbenachrichtigungen verweisen, spiegelt der Textpuffer im Speicher generierter Sie die Änderungen sowie alle weiteren anstehenden Bearbeitungen.  Die Datei auf dem Datenträger gibt den letzten Code, der von Ihnen generierten und alle zuvor gespeicherten Änderungen vom Benutzer in USER\-bearbeitetem Code.  
  
5.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A>\-Methode auf, um das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>\-Objekt der abstrakten überwachung für die Datei änderungsbenachrichtigungen zu benachrichtigen, indem Sie den `fIgnore`\-Parameter `false`festlegen.  
  
6.  Wenn Sie einige Änderungen an der Datei vorzunehmen, z. B. im Falle der Quellcodeverwaltung \(SCC\), müssen Sie dem globalen Datei änderungsdienst verdeutlichen, um änderungsbenachrichtigungen Datei vorübergehend anzuhalten.  
  
     Wenn Sie beispielsweise die Datei neu schreiben und dann den Timestamp geändert haben, müssen Sie die Datei änderungsbenachrichtigungen enthalten, da die einzelnen Vorgänge Neufassungs\- und timestample Geltung als eine separate Datei Ereignis ändern.  Um die globale Datei zu aktivieren änderungsbenachrichtigung sollten Sie stattdessen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A>\-Methode aufrufen.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie änderungsbenachrichtigung Datei unterdrücken.  
  
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
  
## Robuste Programmierung  
 Wenn der Fall mehrere Änderungen an der Datei einschließt, z. B. im Falle SCC, ist es wichtig, globale änderungsbenachrichtigungen Datei vor dem Fortsetzen Alarmieren der Dokumentdaten zur abstrakten überwachung für die Datei ändert.
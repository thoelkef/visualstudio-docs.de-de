---
title: 'Vorgehensweise: Unterdrücken von Datei Änderungs Benachrichtigungen | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204077"
---
# <a name="how-to-suppress-file-change-notifications"></a>Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn die physische Datei, die den Text Puffer darstellt, geändert wurde, wird ein Dialogfeld mit der Meldung angezeigt, **dass die Änderungen an den folgenden Elementen gespeichert** werden sollen? Dies wird als Datei Änderungs Benachrichtigung bezeichnet. Wenn viele Änderungen an der Datei vorgenommen werden sollen, kann dieses Dialogfeld, das immer wieder angezeigt wird, schnell zu lästig werden.  
  
 Dieses Dialogfeld kann mithilfe des folgenden Verfahrens Programm gesteuert unterdrückt werden. Auf diese Weise können Sie eine Datei sofort erneut laden, ohne den Benutzer auffordern zu müssen, die Änderungen jedes Mal zu speichern.  
  
### <a name="to-suppress-file-change-notification"></a>So unterdrücken Sie Datei Änderungs Benachrichtigungen  
  
1. Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode auf, um zu bestimmen, welches Text Puffer Objekt der geöffneten Datei zugeordnet ist.  
  
2. Leiten <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Sie das Objekt, das sich im Arbeitsspeicher befindet, an das Ignorieren von Änderungen an Überwachungs Dateien, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> -Schnittstelle aus dem <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> -Objekt (Dokument Daten) abrufen und dann die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> Methode mit dem- `fIgnore` Parameter `true` in  
  
3. Ruft die-Methoden für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> -Schnittstelle und die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle auf, um das in-Memory- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt mit den Dateiänderungen zu aktualisieren (z. b. Wenn ein Feld der Komponente hinzugefügt wird)  
  
4. Aktualisieren Sie die Datei auf dem Datenträger mit den Änderungen, ohne alle ausstehenden Bearbeitungen zu berücksichtigen, die der Benutzer möglicherweise bearbeitet hat.  
  
     Wenn Sie das Objekt auf diese Weise zum Fortsetzen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Überwachung von Datei Änderungs Benachrichtigungen weiterleiten, reflektiert der Text Puffer im Speicher die von Ihnen generierten Änderungen sowie alle anderen ausstehenden Bearbeitungen. Die Datei auf dem Datenträger gibt den neuesten von Ihnen generierten Code und alle zuvor gespeicherten Änderungen durch den Benutzer in Benutzercode an, der vom Benutzer bearbeitet wurde.  
  
5. Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> Methode, um das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt zu benachrichtigen, die Überwachung von Datei Änderungs Benachrichtigungen fortzusetzen, indem der Parameter auf festgelegt wird `fIgnore` `false` .  
  
6. Wenn Sie mehrere Änderungen an der Datei vornehmen möchten, wie im Fall der Quell Code Verwaltung (Source Code Control, SCC), müssen Sie dem globalen Datei Änderungs Dienst mitteilen, dass Datei Änderungs Benachrichtigungen vorübergehend angehalten werden.  
  
     Wenn Sie z. b. die Datei neu schreiben und dann den Zeitstempel ändern, müssen Sie die Datei Änderungs Benachrichtigungen unterbrechen, da die Vorgänge "rewrite" und "timestample" jeweils als separates Datei Änderungs Ereignis gezählt werden. Um die globale Datei Änderungs Benachrichtigung zu aktivieren, sollten Sie stattdessen die-Methode aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Datei Änderungs Benachrichtigungen unterdrückt werden.  
  
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
 Wenn Ihr Fall mehrere Änderungen an der Datei umfasst, wie im Fall von SCC, ist es wichtig, die globalen Datei Änderungs Benachrichtigungen fortzusetzen, bevor Sie die Dokument Daten warnen, um die Überwachung von Dateiänderungen fortsetzen zu können.

---
title: 'Vorgehensweise: Unterdrücken von Dateiänderungsbenachrichtigungen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7892596af573c777d59f3eb948cdbcc1ffbb72
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702446"
---
# <a name="how-to-suppress-file-change-notifications"></a>Vorgehensweise: Unterdrücken von dateiänderungsbenachrichtigungen
Wenn die physische Datei, die den Textpuffer darstellt geändert wurde, wird ein Dialogfeld anzeigt, mit der Meldung **möchten Sie die folgenden Elemente speichern?** Dies wird als dateiänderungsbenachrichtigung bezeichnet. Wenn viele Änderungen in der Datei werden möchten, kann jedoch dieses Dialogfeld können Sie immer wieder anzeigen schnell lästig werden.

 Sie können dieses Dialogfeld können Sie mit dem folgenden Verfahren programmgesteuert unterdrücken. Durch das Unterdrücken des Dialogfelds, können Sie eine Datei sofort erneut laden ohne den Benutzer auffordern, die Änderungen jedes Mal zu speichern.

## <a name="to-suppress-file-change-notification"></a>Dateiänderungsbenachrichtigung unterdrückt werden sollen.

1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode, um zu bestimmen, welche TextBuffer-Objekt der geöffneten Datei zugeordnet ist.

2.  Direkte der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> -Objekt, das im Arbeitsspeicher, um das ignorieren dateiänderungen durch Abrufen überwacht der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> -Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (Dokumentdaten)-Objekt, und ein anschließendes Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> -Methode mit der `fIgnore` Parameter Legen Sie auf `true`.

3.  Rufen Sie die Methoden auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstellen, die im Arbeitsspeicher aktualisiert <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt mit den Änderungen der Datenbankdatei (z. B. wenn ein Feld für Ihre Komponente hinzugefügt wird).

4.  Aktualisieren Sie die Datei auf dem Datenträger mit den Änderungen, ohne Sie in Betracht ziehen, alle ausstehenden Änderungen, die der Benutzer möglicherweise ausgeführt haben.

     Auf diese Weise, wenn Sie leiten die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> änderungsbenachrichtigungen für Objekt, das Fortsetzen der Überwachung für die Datei, das den Textpuffer im Arbeitsspeicher spiegelt wider, die Änderungen, die Sie erstellt haben. Der Textpuffer im Arbeitsspeicher gibt auch alle anderen ausstehenden Änderungen. Datei auf dem Datenträger Gibt den aktuellen Code, der von Ihnen generierte, und alle Änderungen, die vom Benutzer zuvor im Code bearbeitet werden, Benutzer gespeichert.

5.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> -Methode benachrichtigt die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt, das Fortsetzen der Überwachung für dateiänderungsbenachrichtigungen durch Festlegen der `fIgnore` Parameter, um `false`.

6.  Wenn Sie mehrere Änderungen an der Datei, wie im Fall von quellcodeverwaltung (SCC), vornehmen möchten, müssen Sie die globale dateiänderungsdienst dateiänderungsbenachrichtigungen zeitweise zu unterbrechen mitteilen.

     Z. B. Wenn Sie die Datei schreiben und ändern Sie dann auf den Zeitstempel, müssen Sie die dateiänderungsbenachrichtigungen anzuhalten, da die Vorgänge schreiben und Zeitstempel jeder als eine separate Datei Change-Ereignis gezählt. Um die globale dateiänderungsbenachrichtigung zu aktivieren, rufen Sie stattdessen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> Methode.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie dateiänderungsbenachrichtigung unterdrückt wird.

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
 Wenn umfasst mehrere Änderungen an der Datei, wie im Fall von SCC, das Ihrem Fall ist es wichtig, globale dateiänderungsbenachrichtigungen Warnungen die Dokumentendaten zum Fortsetzen der Überwachung für dateiänderungen fortsetzen.
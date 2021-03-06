---
title: 'Vorgehensweise: Registrieren einer Bibliothek beim Objekt-Manager | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c40c695a912e97269263ba14747b72382847324d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162031"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Gewusst wie: Registrieren einer Bibliothek beim Objekt-Manager
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Symbole: durch Browsen von Tools wie **Klassenansicht**, **Objektkatalog**, **Aufrufbrowser** und **Symbol Ergebnisse**suchen können Sie Symbole in Ihrem Projekt oder in externen Komponenten anzeigen. Zu den Symbolen zählen Namespaces, Klassen, Schnittstellen, Methoden und andere Sprachelemente. Die Bibliotheken verfolgen diese Symbole und machen Sie für den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Objekt-Manager verfügbar, der die Tools mit den Daten füllt.  
  
 Der Objekt-Manager verfolgt alle verfügbaren Bibliotheken nach. Jede Bibliothek muss beim Objekt-Manager registriert werden, bevor Sie Symbole für die Tools zum Durchsuchen von Symbolen bereitstellen.  
  
 In der Regel registrieren Sie eine Bibliothek, wenn ein VSPackage geladen wird. Dies kann jedoch nach Bedarf zu einem anderen Zeitpunkt erfolgen. Sie heben die Registrierung der Bibliothek auf, wenn das VSPackage heruntergefahren wird.  
  
 Verwenden Sie die-Methode, um eine Bibliothek zu registrieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> . Verwenden Sie im Fall der Bibliothek für verwaltete Code die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode.  
  
 Um die Registrierung einer Bibliothek aufzuheben, verwenden Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Methode.  
  
 Um einen Verweis auf den Objekt-Manager zu erhalten, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> übergeben Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Dienst-ID an die- `GetService` Methode.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Registrieren und Aufheben der Registrierung einer Bibliothek beim Objekt-Manager  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>So registrieren Sie eine Bibliothek beim Objekt-Manager  
  
1. Erstellen Sie eine Bibliothek.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2. Rufen Sie einen Verweis auf ein Objekt vom <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> Typ ab, und rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode auf.  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>So heben Sie die Registrierung einer Bibliothek beim Objekt-Manager auf  
  
1. Rufen Sie einen Verweis auf ein Objekt vom <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> Typ ab, und rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Methode auf.  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterbarkeit von Legacy Sprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Unterstützende Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Gewusst wie: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek für den Objekt-Manager bereitgestellt werden](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

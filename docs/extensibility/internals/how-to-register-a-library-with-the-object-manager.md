---
title: 'Gewusst wie: Registrieren einer Bibliothek mit dem Objekt-Manager | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707944"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Gewusst wie: Registrieren einer Bibliothek beim Objektmanager
Mit Tools zum Durchsuchen von Symbolen, z. B. **Klassenansicht**, **Objektbrowser**, **Aufrufbrowser** und **Symbolergebnisse suchen**, können Sie Symbole in Ihrem Projekt oder in externen Komponenten anzeigen. Die Symbole umfassen Namespaces, Klassen, Schnittstellen, Methoden und andere Sprachelemente. Die Bibliotheken verfolgen diese Symbole [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und machen sie für den Objekt-Manager verfügbar, der die Werkzeuge mit den Daten auffüllt.

 Der Objekt-Manager verfolgt alle verfügbaren Bibliotheken. Jede Bibliothek muss sich beim Objekt-Manager registrieren, bevor Symbole für die Symbol-Browsing-Tools zur Verfügung gestellt werden.

 In der Regel registrieren Sie eine Bibliothek, wenn ein VSPackage geladen wird. Dies kann jedoch bei Bedarf zu einem anderen Zeitpunkt erfolgen. Sie heben die Registrierung der Bibliothek auf, wenn das VSPackage heruntergefahren wird.

 Um eine Bibliothek zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> registrieren, verwenden Sie die Methode. Verwenden Sie für eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> verwaltete Codebibliothek die Methode.

 Um die Registrierung einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Bibliothek aufzuheben, verwenden Sie die Methode.

 Um einen Verweis auf den <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>Objekt-Manager abzuerhalten, übergeben Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Dienst-ID an `GetService` die Methode.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registrieren und Aufheben der Registrierung einer Bibliothek beim Objektmanager

### <a name="to-register-a-library-with-the-object-manager"></a>So registrieren Sie eine Bibliothek beim Objektmanager

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

2. Rufen Sie einen Verweis <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> auf ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Objekt des Typs ab, und rufen Sie die Methode auf.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>So heben Sie die Registrierung einer Bibliothek beim Objektmanager auf

1. Rufen Sie einen Verweis <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> auf ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Objekt des Typs ab, und rufen Sie die Methode auf.

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
- [Erweiterbarkeit des Legacy-Sprachdienstes](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Unterstützung von Symbol-Browsing-Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Gewusst wie: Listen mit Symbolen, die von der Bibliothek bereitgestellt werden, für den Objektmanager verfügbar machen](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)

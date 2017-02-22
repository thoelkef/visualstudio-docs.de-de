---
title: "Gewusst wie: Registrieren eine Bibliothek mit der Objekt-Manager | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Objektmanager registriert-Bibliotheken"
  - "Objektmanager Bibliothek registriert IVsLibrary2-Schnittstelle"
  - "Objektmanager Bibliothek registriert IVsSimpleLibrary2-Schnittstelle"
  - "Objektmanager Bibliothek registriert IVsObjectManager2-Schnittstelle"
  - "Tools zum Durchsuchen von Symbol-Bibliotheken"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Registrieren eine Bibliothek mit der Objekt-Manager
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Symbol\-Durchsuchen Tools, z. B. **Klassenansicht**, **Objektkatalog**, **Aufrufbrowser** und **Ergebnisse der Symbolsuche**, können Sie Symbole im Projekt oder in externen Komponenten anzuzeigen.  Die Symbole umfassen Namespaces, Klassen, Schnittstellen, Methoden und anderen Sprachelemente.  Die Bibliotheken nachverfolgt werden diese Symbole und fügen sie dem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Manager Objekt aus der Tools mit den Daten auffüllt.  
  
 Der Objekt Manager verwaltet alle verfügbaren Bibliotheken.  Vor dem Bereitstellen von Symbolen für die einzelnen Tools auf Browse Symbol Bibliothek muss mit dem Objekt Manager registrieren.  
  
 In der Regel VSPackage\-Lasten wenn Sie eine Bibliothek registrieren.  Es kann jedoch auf einen späteren Zeitpunkt nach Bedarf ausgeführt werden.  Markieren Sie die Bibliothek Registrierung wenn ein VSPackage herunterfahren.  
  
 Um eine Bibliothek zu registrieren, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A>\-Methode.  Bei der verwalteten Codebibliothek verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>\-Methode.  
  
 Zum Aufheben der Registrierung einer Bibliothek, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A>\-Methode.  
  
 Um ein Verweis auf das Objekt übergeben, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>Manager, <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> Dienst ID `GetService`\-Methode.  
  
## Eine Bibliothek mit dem Objekt\-Manager registrieren und deren Registrierung aufhebend  
  
#### So erstellen Sie eine Bibliothek mit dem Objekt registrieren Manager  
  
1.  Erstellen einer Bibliothek.  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Rufen Sie einen Verweis auf ein Objekt des Typs <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> und rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>\-Methode veranschaulicht.  
  
    ```vb#  
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
  
    ```c#  
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
  
#### So erstellen Sie eine Bibliothek mit dem Objekt Manager Registrierung aufheben  
  
1.  Rufen Sie einen Verweis auf ein Objekt des Typs <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> und rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A>\-Methode auf.  
  
    ```vb#  
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
  
    ```c#  
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
  
## Siehe auch  
 [Ältere Sprache Service\-Erweiterbarkeit](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Unterstützung von Tools zum Durchsuchen des Symbols](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Gewusst wie: Listen von Symbolen, die von der Bibliothek bereitgestellt, der Objekt\-Manager verfügbar machen](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
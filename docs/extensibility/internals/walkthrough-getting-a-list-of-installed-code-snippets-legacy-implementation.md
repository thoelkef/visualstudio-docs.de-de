---
title: Abrufen einer Liste der installierten Codeausschnitte (Legacy) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4b09968ea178869dd9a4c6f1caeee83f60f667e3
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513243"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)
Ein Codeausschnitt ist ein Codeabschnitt, der eingefügt werden können, in den Quellpuffer mit einem Menübefehl (mit der können eine Liste der installierten Codeausschnitte Auswahl) oder durch eine ausschnittsverknüpfung aus einer IntelliSense-Vervollständigungsliste auswählen.  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Methode ruft alle Codeausschnitte für eine bestimmte Sprache GUID ab. Die Tastenkombinationen für diese Codeausschnitte können in einer IntelliSense-Vervollständigungsliste eingefügt werden.  
  
 Finden Sie unter [Unterstützung für Codeausschnitte in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) ausführliche Informationen zum Implementieren von Codeausschnitten in einem verwalteten Paket Framework (MPF)-Sprachdienst.  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>Zum Abrufen einer Liste von Codeausschnitten  
  
1.  Der folgende Code zeigt, wie Sie eine Liste von Codeausschnitten für eine bestimmte Sprache zu erhalten. Die Ergebnisse werden gespeichert, in ein Array von <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> Strukturen. Diese Methode verwendet die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> -Methode zum Abrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> -Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Service. Allerdings können Sie auch den Dienstanbieter übergeben, um Ihr VSPackage, und rufen verwenden die <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> Methode.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>Zum Aufrufen der GetSnippets-Methode  
  
1.  Die folgende Methode wird das Aufrufen der `GetSnippets` Methode nach dem Abschluss von einem Analysevorgang. Die <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Methode wird aufgerufen, nachdem einem Analysevorgang, der mit dem Grund gestartet wurde <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
> [!NOTE]
>  Die `expansionsList` Array-Liste wird aus Leistungsgründen zwischengespeichert. Änderungen an der Codeausschnitte werden nicht in der Liste wiedergegeben, wenn der Sprachdienst beendet und neu geladen wird (z. B. durch Anhalten und Neustarten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>Verwenden Sie die Snippet-Informationen  
  
1.  Der folgende Code zeigt, wie Sie mit der zurückgegebenen Informationen Ausschnitt der `GetSnippets` Methode. Die `AddSnippets` Methode wird aufgerufen, vom Parser als Reaktion auf irgendwelchen analysieren, die zum Auffüllen einer Liste von Codeausschnitten verwendet wird. Dies sollte erfolgen, nachdem die vollständige Analyse zum ersten Mal erfolgt ist.  
  
     Die `AddDeclaration` Methode erstellt eine Liste der Deklarationen, die später in eine Vervollständigungsliste angezeigt wird.  
  
     Die `TestDeclaration` Klasse enthält alle Informationen, die in eine Vervollständigungsliste sowie den Typ der Deklaration angezeigt werden kann.  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
---
title: Abrufen einer Liste der installierten Codeausschnitte (Legacy) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703657"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)
Ein Codeausschnitt ist ein Codeteil, der entweder mit einem Menübefehl (der die Auswahl zwischen einer Liste installierter Codeausschnitte ermöglicht) oder durch Auswählen einer Codeausschnittverknüpfung aus einer IntelliSense-Vervollständigungsliste in den Quellpuffer eingefügt werden kann.

 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Methode ruft alle Codeausschnitte für eine bestimmte Sprach-GUID ab. Die Verknüpfungen für diese Ausschnitte können in eine IntelliSense-Vervollständigungsliste eingefügt werden.

 Weitere Informationen zum Implementieren von Codeausschnitten in einem MPF-Sprachdienst (Managed Package Framework, MPF) finden Sie unter [Support für Codeausschnitte in einem Legacy-Sprachdienst.](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

### <a name="to-retrieve-a-list-of-code-snippets"></a>So rufen Sie eine Liste von Codeausschnitten ab

1. Der folgende Code zeigt, wie Sie eine Liste von Codeausschnitten für eine bestimmte Sprache abrufen. Die Ergebnisse werden in <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> einer Reihe von Strukturen gespeichert. Diese Methode verwendet <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> die statische <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Methode, <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> um die Schnittstelle vom Dienst abzubekommen. Sie können jedoch auch den Dienstanbieter verwenden, der <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> Ihrem VSPackage gegeben wurde, und die Methode aufrufen.

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

### <a name="to-call-the-getsnippets-method"></a>So rufen Sie die GetSnippets-Methode auf

1. Die folgende Methode zeigt, `GetSnippets` wie die Methode nach Abschluss eines Analysevorgangs aufruft. Die <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Methode wird nach einem Analysevorgang aufgerufen, <xref:Microsoft.VisualStudio.Package.ParseReason>der mit dem Grund gestartet wurde.

> [!NOTE]
> Die `expansionsList` Arrayliste wird aus Leistungsgründen zwischengespeichert. Änderungen an den Ausschnitten werden erst in der Liste widergespiegelt, wenn der Sprachdienst [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]angehalten und neu geladen wurde (z. B. durch Beenden und Neustarten ).

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

### <a name="to-use-the-snippet-information"></a>So verwenden Sie die Snippet-Informationen

1. Der folgende Code zeigt, wie die von der `GetSnippets` Methode zurückgegebenen Ausschnittinformationen verwendet werden. Die `AddSnippets` Methode wird vom Parser als Antwort auf jeden Analysegrund aufgerufen, der zum Auffüllen einer Liste von Codeausschnitten verwendet wird. Dies sollte erfolgen, nachdem die vollständige Analyse zum ersten Mal durchgeführt wurde.

     Die `AddDeclaration` Methode erstellt eine Liste von Deklarationen, die später in einer Abschlussliste angezeigt werden.

     Die `TestDeclaration` Klasse enthält alle Informationen, die in einer Vervollständigungsliste angezeigt werden können, sowie den Deklarationstyp.

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

## <a name="see-also"></a>Weitere Informationen
- [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

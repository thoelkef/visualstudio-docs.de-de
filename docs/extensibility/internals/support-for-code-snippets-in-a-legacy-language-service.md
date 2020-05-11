---
title: Unterstützung für Codeausschnitte in einem Legacy Language Service | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704910"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Unterstützen von Codeausschnitten in einem Legacysprachdienst
Ein Codeausschnitt ist ein Code, der in die Quelldatei eingefügt wird. Der Ausschnitt selbst ist eine XML-basierte Vorlage mit einer Reihe von Feldern. Diese Felder werden nach dem Einfügen des Ausschnitts hervorgehoben und können je nach Kontext, in den der Ausschnitt eingefügt wird, unterschiedliche Werte aufweisen. Unmittelbar nach dem Einfügen des Ausschnitts kann der Sprachdienst den Ausschnitt formatieren.

 Der Ausschnitt wird in einen speziellen Bearbeitungsmodus eingefügt, der es ermöglicht, die Felder des Ausschnitts mithilfe der TAB-Taste zu navigieren. Die Felder können Dropdown-Menüs im IntelliSense-Stil unterstützen. Der Benutzer überträgt den Ausschnitt in die Quelldatei, indem er entweder die ENTER- oder die ESC-Taste eingibt. Weitere Informationen zu Snippets finden Sie unter [Code Snippets](../../ide/code-snippets.md).

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework-Unterstützung für Codeausschnitte
 Das Verwaltete Paketframework (Managed Package Framework, MPF) unterstützt die meisten Snippet-Funktionen, vom Lesen der Vorlage über das Einfügen des Snippets bis hin zum Aktivieren des speziellen Bearbeitungsmodus. Die Unterstützung wird <xref:Microsoft.VisualStudio.Package.ExpansionProvider> über die Klasse verwaltet.

 Wenn <xref:Microsoft.VisualStudio.Package.Source> die Klasse instanziiert <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> wird, <xref:Microsoft.VisualStudio.Package.LanguageService> wird die Methode <xref:Microsoft.VisualStudio.Package.ExpansionProvider> in der Klasse <xref:Microsoft.VisualStudio.Package.LanguageService> aufgerufen, um <xref:Microsoft.VisualStudio.Package.ExpansionProvider> ein Objekt <xref:Microsoft.VisualStudio.Package.Source> abzusondern (beachten Sie, dass die Basisklasse immer ein neues Objekt für jedes Objekt zurückgibt).

 Die MPF unterstützt keine Erweiterungsfunktionen. Eine Erweiterungsfunktion ist eine benannte Funktion, die in eine Ausschnittvorlage eingebettet ist und einen oder mehrere Werte zurückgibt, die in einem Feld platziert werden sollen. Die Werte werden vom Sprachdienst <xref:Microsoft.VisualStudio.Package.ExpansionFunction> selbst über ein Objekt zurückgegeben. Das <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt muss vom Sprachdienst implementiert werden, um Erweiterungsfunktionen zu unterstützen.

## <a name="providing-support-for-code-snippets"></a>Unterstützung für Codeausschnitte
 Um die Unterstützung für Codeausschnitte zu aktivieren, müssen Sie die Ausschnitte bereitstellen oder installieren, und Sie müssen dem Benutzer die Möglichkeit zur Verfügung stellen, diese Ausschnitte einzufügen. Es gibt drei Schritte, um die Unterstützung für Codeausschnitte zu aktivieren:

1. Installieren der Snippet-Dateien.

2. Aktivieren von Codeausschnitten für Ihren Sprachdienst.

3. Aufrufen des <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekts.

### <a name="installing-the-snippet-files"></a>Installieren der Snippet-Dateien
 Alle Ausschnitte für eine Sprache werden als Vorlagen in XML-Dateien gespeichert, in der Regel eine Snippet-Vorlage pro Datei. Weitere Informationen zum XML-Schema, das für Codeausschnittvorlagen verwendet wird, finden Sie unter [Codesnippets Schema Reference](../../ide/code-snippets-schema-reference.md). Jede Ausschnittvorlage wird mit einer Sprach-ID gekennzeichnet. Diese Sprach-ID wird in der Registrierung `Language` angegeben \<und in das Attribut des Code->-Tags in der Vorlage eingefügt.

 Es gibt in der Regel zwei Speicherorte, an denen Snippet-Vorlagendateien gespeichert werden: 1) wo Ihre Sprache installiert wurde, und 2) im Ordner des Benutzers. Diese Speicherorte werden der Registrierung hinzugefügt, damit der Visual Studio **Code Snippets Manager** die Ausschnitte finden kann. Im Ordner des Benutzers werden vom Benutzer erstellte Ausschnitte gespeichert.

 Das typische Ordnerlayout für die installierten Snippet-Vorlagendateien sieht wie folgt aus:\\ *[LCID]* *[InstallRoot]*\\ *[TestLanguage]*

 *[InstallRoot]* ist der Ordner, in dem Ihre Sprache installiert ist.

 *[TestLanguage]* ist der Name Ihrer Sprache als Ordnername.

 *[LCID]* ist die Gebietsschema-ID. Auf diese Weise werden lokalisierte Versionen Ihrer Snippets gespeichert. Die Gebietsschema-ID für Englisch ist z. B. 1033, daher wird *[LCID]* durch 1033 ersetzt.

 Eine zusätzliche Datei muss angegeben werden, und das ist eine Indexdatei, in der Regel SnippetsIndex.xml oder ExpansionsIndex.xml genannt (Sie können jeden gültigen Dateinamen verwenden, der auf .xml endet). Diese Datei wird in der Regel im Ordner *[InstallRoot]*\\ *[TestLanguage]* gespeichert und gibt den genauen Speicherort des Snippets-Ordners sowie die Sprach-ID und GUID des Sprachdienstes an, der die Snippets verwendet. Der genaue Pfad der Indexdatei wird wie weiter unten unter "Installieren der Registrierungseinträge" in die Registrierung eingetragen. Hier ist ein Beispiel für eine Datei SnippetsIndex.xml:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 Das \<Language>-Tag gibt die `Lang` Sprach-ID (das Attribut) und die GUID des Sprachdienstes an.

 In diesem Beispiel wird davon ausgegangen, dass Sie den Sprachdienst im Visual Studio-Installationsordner installiert haben. %LCID% wird durch die aktuelle Gebietsschema-ID des Benutzers ersetzt. Mehrere \<SnippetDir-> Tags können hinzugefügt werden, eines für jedes einzelne Verzeichnis und Gebietsschema. Darüber hinaus kann ein Ausschnittordner Unterordner enthalten, von denen jeder in \<der Indexdatei mit dem SnippetSubDir->-Tag identifiziert wird, der in ein \<SnippetDir->-Tag eingebettet ist.

 Benutzer können auch eigene Ausschnitte für Ihre Sprache erstellen. Diese werden in der Regel im Einstellungsordner des Benutzers gespeichert, z. B. *[TestDocs]*. *[TestDocs]* . . . . . . . . . . .\\ *.*. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

 Die folgenden Ersetzungselemente können in \<dem Pfad platziert werden, der im DirPath>-Tag in der Indexdatei gespeichert ist.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|%LCID%|Gebietsschema-ID.|
|%InstallRoot%|Stamminstallationsordner für Visual Studio, z. B. C:-Programmdateien, Microsoft Visual Studio 8.|
|%ProjDir%|Ordner, der das aktuelle Projekt enthält.|
|%ProjItem%|Ordner, der das aktuelle Projektelement enthält.|
|%TestDocs%|Ordner im Einstellungsordner des Benutzers, z. B. C:-Dokumente und -Einstellungen\\ *[Benutzername]*,,Eigene Dokumente, Visual Studio,8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Aktivieren von Codeausschnitten für Ihren Sprachdienst
 Sie können Codeausschnitte für Ihren Sprachdienst <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aktivieren, indem Sie das Attribut zu Ihrem VSPackage hinzufügen (Details finden Sie unter [Registrieren eines Legacy-Sprachdienstes).](../../extensibility/internals/registering-a-legacy-language-service1.md) Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> und Parameter sind optional, `SearchPaths` aber Sie sollten den benannten Parameter einschließen, um den **Codesnippets Manager** über den Speicherort Ihrer Ausschnitte zu informieren.

 Im Folgenden finden Sie ein Beispiel für die Verwendung dieses Attributs:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Aufrufen des Erweiterungsanbieters
 Der Sprachdienst steuert das Einfügen eines beliebigen Codeausschnitts sowie die Art und Weise, wie das Einfügen aufgerufen wird.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Aufrufen des Erweiterungsanbieters für Codeausschnitte
 Es gibt zwei Möglichkeiten, den Erweiterungsanbieter aufzurufen: mithilfe eines Menübefehls oder mithilfe einer Verknüpfung aus einer Abschlussliste.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Einfügen eines Codeausschnitts mithilfe eines Menübefehls
 Um einen Menübefehl zum Anzeigen des Snippet-Browsers zu <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> verwenden, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> fügen Sie einen Menübefehl hinzu und rufen dann die Methode in der Schnittstelle als Antwort auf diesen Menübefehl auf.

1. Fügen Sie Ihrer .vsct-Datei einen Befehl und eine Schaltfläche hinzu. Anweisungen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Leiten Sie eine <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> Klasse ab, und überschreiben Sie die Methode, um die Unterstützung für den neuen Menübefehl anzugeben. In diesem Beispiel wird immer der Menübefehl aktiviert.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. Überschreiben <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> Sie die <xref:Microsoft.VisualStudio.Package.ViewFilter> Methode in <xref:Microsoft.VisualStudio.Package.ExpansionProvider> der Klasse, um das Objekt abzurufen, und rufen Sie die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode für dieses Objekt auf.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Die folgenden Methoden <xref:Microsoft.VisualStudio.Package.ExpansionProvider> in der Klasse werden von Visual Studio in der angegebenen Reihenfolge aufgerufen, während der Daseinfügt der Ausschnitt:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Nachdem <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> die Methode aufgerufen wurde, wurde der Ausschnitt <xref:Microsoft.VisualStudio.Package.ExpansionProvider> eingefügt, und das Objekt befindet sich in einem speziellen Bearbeitungsmodus, der zum Ändern eines soeben eingefügten Ausschnitts verwendet wird.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Einfügen eines Codeausschnitts mithilfe einer Verknüpfung
 Die Implementierung einer Verknüpfung aus einer Vervollständigungsliste ist viel wichtiger als die Implementierung eines Menübefehls. Sie müssen der IntelliSense-Wortvervollständigungsliste zunächst Snippet-Verknüpfungen hinzufügen. Anschließend müssen Sie erkennen, wann ein Codenippet-Verknüpfungsname als Ergebnis der Fertigstellung eingefügt wurde. Schließlich müssen Sie den Codeausschnitttitel und -pfad mithilfe des Verknüpfungsnamens abrufen und diese Informationen an die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Methode übergeben.

 Um der Liste der Wortvervollständigung Snippet-Verknüpfungen hinzuzufügen, fügen Sie sie dem <xref:Microsoft.VisualStudio.Package.Declarations> Objekt in Ihrer <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse hinzu. Sie müssen sicherstellen, dass Sie die Verknüpfung als Ausschnittnamen identifizieren können. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste installierter Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Sie können das Einfügen der Codeausschnittverknüpfung in <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> die <xref:Microsoft.VisualStudio.Package.Declarations> Methode der Klasse erkennen. Da der Codeausschnittname bereits in die Quelldatei eingefügt wurde, muss er beim Einfügen der Erweiterung entfernt werden. Die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode nimmt eine Spanne, die den Punkt der Einfügung für den Ausschnitt beschreibt. Wenn die Spanne den gesamten Codenippet-Namen in der Quelldatei enthält, wird dieser Name durch den Ausschnitt ersetzt.

 Hier ist eine <xref:Microsoft.VisualStudio.Package.Declarations> Version einer Klasse, die das Einfügen von Ausschnitten mit einem Verknüpfungsnamen verarbeitet. Andere Methoden <xref:Microsoft.VisualStudio.Package.Declarations> in der Klasse wurden aus Gründen der Übersichtlichkeit weggelassen. Beachten Sie, dass der Konstruktor dieser Klasse ein <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt annimmt. Dies kann von Ihrer Version <xref:Microsoft.VisualStudio.Package.AuthoringScope> des Objekts übergeben werden <xref:Microsoft.VisualStudio.Package.AuthoringScope> (z. <xref:Microsoft.VisualStudio.Package.LanguageService> B. kann Ihre Implementierung der `TestDeclarations` Klasse das Objekt in ihrem Konstruktor übernehmen und dieses Objekt an den Klassenkonstruktor weitergeben).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Wenn der Sprachdienst den Verknüpfungsnamen <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> erhält, ruft er die Methode auf, um den Dateinamen- und Codeausschnitttitel abzusichern. Der Sprachdienst ruft <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> dann <xref:Microsoft.VisualStudio.Package.ExpansionProvider> die Methode in der Klasse auf, um den Codeausschnitt einzufügen. Die folgenden Methoden werden von Visual Studio <xref:Microsoft.VisualStudio.Package.ExpansionProvider> in der angegebenen Reihenfolge in der Klasse aufgerufen, während der Snippet eingefügt wird:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Weitere Informationen zum Abrufen einer Liste installierter Codeausschnitte für Ihren Sprachdienst finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste installierter Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementieren der Erweiterungsfunktionsklasse
 Eine Erweiterungsfunktion ist eine benannte Funktion, die in eine Ausschnittvorlage eingebettet ist und einen oder mehrere Werte zurückgibt, die in einem Feld platziert werden sollen. Um Erweiterungsfunktionen in Ihrem Sprachdienst zu unterstützen, müssen <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Sie eine <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> Klasse aus der Klasse ableiten und die Methode implementieren. Sie müssen dann <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> die Methode <xref:Microsoft.VisualStudio.Package.LanguageService> in der Klasse überschreiben, um <xref:Microsoft.VisualStudio.Package.ExpansionFunction> für jede von Ihnen unterstützte Erweiterungsfunktion eine neue Instanziierung Ihrer Version der Klasse zurückzugeben. Wenn Sie eine Liste möglicher Werte aus einer Erweiterungsfunktion <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> unterstützen, <xref:Microsoft.VisualStudio.Package.ExpansionFunction> müssen Sie auch die Methode in der Klasse überschreiben, um eine Liste dieser Werte zurückzugeben.

 Eine Erweiterungsfunktion, die Argumente verwendet oder auf andere Felder zugreifen muss, sollte keinem bearbeitbaren Feld zugeordnet werden, da der Erweiterungsanbieter möglicherweise nicht vollständig initialisiert wird, wenn die Erweiterungsfunktion aufgerufen wird. Daher ist die Erweiterungsfunktion nicht in der Lage, den Wert ihrer Argumente oder eines anderen Feldes zu erhalten.

### <a name="example"></a>Beispiel
 Hier ist ein Beispiel dafür, `GetName` wie eine einfache Erweiterungsfunktion namens implementiert werden könnte. Diese Erweiterungsfunktion fügt jedes Mal, wenn die Erweiterungsfunktion instanziiert wird, eine Zahl an einen Basisklassennamen anhängen (was jedem Einfügen des zugeordneten Codeausschnitts entspricht).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Codeausschnitte](../../ide/code-snippets.md)
- [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

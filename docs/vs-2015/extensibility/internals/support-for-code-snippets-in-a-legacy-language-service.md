---
title: Unterstützung für Codeausschnitte in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d0ca68c9d95f0b2b511ece0ecafbd9bdcacf328d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947429"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Unterstützen von Codeausschnitten in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Codeausschnitt ist ein Codeabschnitt, der in die Quelldatei eingefügt wird. Des Codeausschnitts selbst ist eine XML-basierte Vorlage mit einem Satz von Feldern. Diese Felder werden hervorgehoben, nachdem der Codeausschnitt eingefügt und haben unterschiedliche Werte je nach Kontext, in dem der Ausschnitt eingefügt wird. Sofort, nachdem der Codeausschnitt eingefügt wird, kann der Sprachdienst im Codeausschnitt formatieren.  
  
 Der Codeausschnitt wird in einer speziellen Bearbeitungsmodus eingefügt, die die Felder des Ausschnitts, um mit der TAB-Taste navigiert werden können. Die Felder können IntelliSense-Stil Dropdown-Menüs unterstützt werden. Der Benutzer führt einen Commit für den Codeausschnitt zur Quelldatei Geben Sie entweder die EINGABETASTE oder die ESC-Taste. Weitere Informationen zu Codeausschnitten finden Sie unter [Codeausschnitte](../../ide/code-snippets.md).  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework-Unterstützung für Codeausschnitte  
 Das managed Package Framework (MPF) unterstützt die meisten Funktionen für den Codeausschnitt, lesen Sie die Vorlage, die den Ausschnitt eingefügt, und aktivieren die spezielle Bearbeitungsmodus. Support wird über verwaltet die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse.  
  
 Wenn der <xref:Microsoft.VisualStudio.Package.Source> Klasse instanziiert wird, die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> -Methode in der der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse aufgerufen, um erhalten ein <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt (Beachten Sie, dass die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse gibt immer eine neue <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt für jede <xref:Microsoft.VisualStudio.Package.Source> -Objekt).  
  
 Das MPF unterstützt Erweiterungsfunktionen nicht. Eine Erweiterungsfunktion ist eine benannte Funktion, die in einem Ausschnittvorlage eingebettet ist, und gibt einen oder mehrere Werte in einem Feld platziert werden. Die Werte werden zurückgegeben, von der Sprache selbst über eine <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt. Die <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt muss vom Sprachdienst zur Unterstützung von Erweiterungsfunktionen implementiert werden.  
  
## <a name="providing-support-for-code-snippets"></a>Bereitstellen von Unterstützung für Codeausschnitte  
 Um Unterstützung für Codeausschnitte aktivieren, müssen Sie bereitstellen oder installieren Sie die Codeausschnitte, und Sie müssen angeben, das bedeutet, dass der Benutzer diese Ausschnitte einfügen. Es gibt drei Schritte zum Aktivieren der Unterstützung für Codeausschnitte aus:  
  
1.  Installieren die codeausschnittsdateien an.  
  
2.  Aktivieren Codeausschnitte für den Sprachdienst.  
  
3.  Aufrufen der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt.  
  
### <a name="installing-the-snippet-files"></a>Installieren die Codeausschnittsdateien  
 Alle Codeausschnitte für eine Sprache werden als Vorlagen im XML-Dateien, in der Regel eine Ausschnittvorlage pro Datei gespeichert. Ausführliche Informationen zu den XML-Schema für Codeausschnittvorlagen verwendet, finden Sie unter [Schemareferenz für Codeausschnitte](../../ide/code-snippets-schema-reference.md). Jede Vorlage Codeausschnitt wird mit einer Sprachen-ID identifiziert. Diese Sprache-ID in der Registrierung angegeben ist und in den versetzt wird die `Language` Attribut der \<Code > Tag in der Vorlage.  
  
 Es gibt in der Regel zwei Orten, in dem Codeausschnitt-Vorlagendateien gespeichert sind: (1), wo Ihre Sprache installiert wurde, und klicken Sie mit der 2) in den Ordner des Benutzers. Diese Speicherorte werden der Registrierung hinzugefügt also, die Visual Studio **Codeausschnitt-Manager** finden Sie die Codeausschnitte. Im Ordner des Benutzers ist, in dem vom Benutzer erstellte Codeausschnitte gespeichert werden.  
  
 Typische ordnerlayouts für die installierte Vorlage codeausschnittsdateien sieht wie folgt aus: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.  
  
 *[InstallRoot]*  ist der Ordner, in die Sprache installiert ist.  
  
 *[TestLanguage]*  ist der Name der Sprache als einen Ordnernamen ein.  
  
 *[LCID]*  ist die Gebietsschema-ID. Dies ist wie lokalisierte Versionen Ausschnitte werden gespeichert. Die Gebietsschema-ID für Englisch ist beispielsweise 1033, also *[LCID]* durch 1033 ersetzt wird.  
  
 Eine zusätzliche Datei muss angegeben werden, und eine Indexdatei, die in der Regel als SnippetsIndex.xml oder ExpansionsIndex.xml (Sie können jeden gültigen Dateinamen mit der Endung XML verwenden) bezeichnet wird. Diese Datei befindet sich in der Regel in der *[InstallRoot]*\\ *[TestLanguage]* Ordner und gibt den genauen Speicherort der Codeausschnittordner als auch die Sprach-ID und GUID der Sprache Dienst, der die Codeausschnitte verwendet. Der genaue Pfad der Indexdatei wird in der Registrierung eingefügt, wie weiter unten in "Installieren der Registrierungseinträge" beschrieben. Hier ist ein Beispiel einer SnippetsIndex.xml-Datei:  
  
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
  
 Die \<Sprache >-Tag gibt die Sprach-ID (die `Lang` Attribut) und der Sprachdienst-GUID.  
  
 In diesem Beispiel wird davon ausgegangen, dass Sie Ihren Sprachdienst im Visual Studio-Installationsordner installiert haben. Der % LCID % wird mit dem aktuellen Gebietsschema-ID des Benutzers ersetzt. Mehrere \<SnippetDir > Tags hinzugefügt werden können, eine für jedes anderen Verzeichnis und Gebietsschema. Darüber hinaus darf ein ausschnittordners Unterordner aus, von denen jede wird in der Indexdatei mit identifiziert die \<SnippetSubDir >-Tag, das in eingebettet ist eine \<SnippetDir > Tag.  
  
 Benutzer können auch ihre eigenen Codeausschnitte für Ihre Sprache erstellen. Diese werden in der Regel gespeichert im Ordner "Einstellungen" des Benutzers, z. B. *[TestDocs]* \Code Codeausschnitte\\ *[TestLanguage]* \Test Codeausschnitte, in denen *[TestDocs]* ist der Speicherort des Ordners "Einstellungen" des Benutzers für Visual Studio.  
  
 Die folgenden Ersetzungselemente platziert werden können, in dem Pfad gespeichert, der \<DirPath >-Tag in der Indexdatei.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|% LCID %|Gebietsschema-ID.|  
|%InstallRoot%|Stamminstallationsordners für Visual Studio, z. B. c:\Programme\Microsoft c:\Programme\Microsoft Visual Studio 8.|  
|%ProjDir%|Ordner mit dem aktuellen Projekt.|  
|%ProjItem%|Dieser Ordner enthält das aktuelle Projektelement.|  
|%TestDocs%|Im Ordner "Einstellungen" des Benutzers, z. B. C:\Documents and Settings\\ *[Username]* \My Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Aktivieren Codeausschnitte für Ihren Sprachdienst  
 Sie können Codeausschnitte für den Sprachdienst aktivieren, durch das Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> Attribut für das VSPackage (finden Sie unter [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md) Einzelheiten). Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> und <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> Parameter sind optional, aber Sie sollten einschließen, die `SearchPaths` benannter Parameter, um zu den **Codeausschnitt-Manager** des Speicherorts für Ihre Ausschnitte.  
  
 Im folgenden finden ein Beispiel zur Verwendung dieses Attributs:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Die Erweiterungsanbieter aufrufen  
 Der Sprachdienst steuert das Einfügen von alle Codeausschnitte als auch die Möglichkeit, die Einfügemarke aufgerufen wird.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Aufrufen von Erweiterungsanbieter für Codeausschnitte  
 Es gibt zwei Möglichkeiten zum Aufrufen der Erweiterungsanbieter: mithilfe eines Menübefehls oder mithilfe einer Verknüpfung aus einer Vervollständigungsliste.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Einfügen eines Codeausschnitts mithilfe eines Menübefehls  
 Um einen Befehl verwenden, um die im Codeausschnitt-Browser angezeigt werden, Sie fügen Sie einen Menübefehl hinzu, und rufen dann die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Schnittstelle als Reaktion auf dieser Menübefehl.  
  
1.  Fügen Sie einen Befehl und eine Schaltfläche, um Ihre VSCT-Datei. Finden Sie Anweisungen zum Ausführen in [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio-Paketvorlage](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
2.  Leiten Sie eine Klasse aus der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse, und überschreiben die <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> Methode, um Unterstützung für den neuen Menübefehl anzugeben. In diesem Beispiel wird immer den Menübefehl aus.  
  
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
  
3.  Überschreiben der <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse zum Abrufen der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt, und rufen die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode für dieses Objekt.  
  
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
  
     Die folgenden Methoden in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse werden von Visual Studio in der angegebenen Reihenfolge aufgerufen, während des Prozesses, der den Ausschnitt eingefügt:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Nach der <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> Methode aufgerufen wird, wird der Codeausschnitt eingefügt wurde und die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt befindet sich in einer speziellen Bearbeitungsmodus zum Ändern eines Codeausschnitts, der gerade eingefügt wurde.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Einfügen eines Codeausschnitts mithilfe einer Verknüpfung  
 Eine Verknüpfung aus einer Vervollständigungsliste Implementierung ist sehr viel komplizierter als die Implementierung eines Menübefehls. Sie müssen zuerst die IntelliSense-Vervollständigungsliste für Word ausschnittsverknüpfungen hinzufügen. Dann müssen Sie erkennen, wenn als Ergebnis der Abschluss ein ausschnittnamens für die Verknüpfung eingefügt wurde. Abschließend müssen Sie den Codeausschnitt-Titel und den Pfad, die mithilfe von Abkürzungsnamen zu erhalten und übergeben Sie die Informationen in den <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Methode.  
  
 Ausschnittsverknüpfungen in die Vervollständigungsliste für Word hinzufügen möchten, fügen sie der <xref:Microsoft.VisualStudio.Package.Declarations> -Objekt in Ihrem <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse. Sie müssen sicherstellen, dass Sie die Verknüpfung als einen Codeausschnittnamen ein identifizieren können. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Sie können erkennen, dass das Einfügen der Verknüpfung des Code-Ausschnitt in die <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> Methode der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Da in der Quelldatei bereits den Namen des Ausschnitts eingefügt wurde, muss er entfernt werden, wenn die Erweiterung eingefügt wird. Die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode akzeptiert eine Spanne, die beschreibt, der Einfügemarke für den Ausschnitt, wenn die Spanne der gesamte Ausschnitt-Name in der Quelldatei enthält, wird dieser Name von dem Ausschnitt ersetzt.  
  
 Hier ist eine Version von einem <xref:Microsoft.VisualStudio.Package.Declarations> Klasse, erhält einen Verknüpfungsnamen Einfügen von Codeausschnitten verarbeitet. Andere Methoden in der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse wurde aus Gründen der Übersichtlichkeit weggelassen. Beachten Sie, die der Konstruktor dieser Klasse verwendet eine <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt. Dies kann von Ihrer Version des übergeben werden die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt (z. B. die Implementierung von der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse dauern die <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt in seinem Konstruktor, und übergeben Sie das Objekt auf Ihre `TestDeclarations` Klassenkonstruktor).  
  
```  
[C#]  
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
  
 Wenn der Sprachdienst den Verknüpfungsnamen abruft, ruft er die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> Methode, um den Dateinamen und den Code Snippet Titel abzurufen. Der Sprachdienst ruft dann die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse, um den Codeausschnitt einzufügen. Die folgenden Methoden werden von Visual Studio aufgerufen, in der angegebenen Reihenfolge in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse während des Prozesses, der den Ausschnitt eingefügt:  
  
1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
   Weitere Informationen zum Abrufen einer Liste der installierten Codeausschnitte für den Sprachdienst, finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementieren der ExpansionFunction-Klasse  
 Eine Erweiterungsfunktion ist eine benannte Funktion, die in einem Ausschnittvorlage eingebettet ist, und gibt einen oder mehrere Werte in einem Feld platziert werden. Um Erweiterungsfunktionen in den Sprachdienst zu unterstützen, müssen Sie leiten eine Klasse von der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse und Implementieren der <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> Methode. Dann müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse die Rückgabe einer neuen Instanziierung von Ihrer Version von der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse für jede Erweiterungsfunktion, die Sie unterstützen. Wenn Sie eine Liste der möglichen Werte aus einer Erweiterungsfunktion unterstützen, müssen Sie auch überschreiben die <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse um eine Liste dieser Werte zurückzugeben.  
  
 Eine Erweiterungsfunktion, die Argumente akzeptiert, oder auf andere Felder zugreifen muss darf nicht bearbeitbares Feld, zugeordnet sein, wie die Erweiterungsanbieter nicht vollständig mit der Zeit initialisiert werden kann, die die Erweiterungsfunktion aufgerufen wird. Daher kann die Erweiterungsfunktion nicht den Wert der Argumente oder ein anderes Feld abzurufen.  
  
### <a name="example"></a>Beispiel  
 Es folgt ein Beispiel, wie eine einfache Erweiterungsfunktion aufgerufen `GetName` implementiert werden könnte. Diese Erweiterungsfunktion Fügt eine Zahl in einen Namen für die Basisklasse jedes Mal, das die Erweiterungsfunktion instanziiert wird (wird eingefügt, wenn sich den zugehörige Code-Ausschnitt entspricht).  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Codeausschnitte](../../ide/code-snippets.md)   
 [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

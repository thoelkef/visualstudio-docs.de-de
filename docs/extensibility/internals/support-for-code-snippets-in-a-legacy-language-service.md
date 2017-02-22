---
title: "Unterst&#252;tzung f&#252;r Codeausschnitte in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausschnitte in Language Services unterstützen"
  - "Codeausschnitte, die Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "Sprachdienste [Verwaltetes Paketframework], Unterstützung von Codeausschnitten"
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Unterst&#252;tzung f&#252;r Codeausschnitte in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Codeausschnitt ist ein Codeabschnitt, der in die Quelldatei eingefügt wird. Der Codeausschnitt selbst ist eine XML\-basierte Vorlage mit einem Satz von Feldern. Diese Felder werden hervorgehoben, nachdem der Codeausschnitt eingefügt und kann verschiedene Werte je nach Kontext, in dem der Ausschnitt eingefügt wird. Sofort, nachdem der Codeausschnitt eingefügt wird, kann der Sprachdienst den Ausschnitt formatieren.  
  
 Der Ausschnitt wird in eine spezielle Bearbeitungsmodus eingefügt, mit dem die Felder des Ausschnitts, um mithilfe der TAB\-Taste navigiert werden können. Die Felder können IntelliSense\-Stil Dropdown\-Menüs unterstützt. Der Benutzer führt einen Commit für den Codeausschnitt an der Quelldatei durch Drücken der EINGABETASTE oder ESC\-Taste. Weitere Informationen zu Codeausschnitten finden Sie unter [Codeausschnitte](../../ide/code-snippets.md).  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Managed Package Framework\-Unterstützung für Codeausschnitte  
 Das Paketframework für verwalteten \(MPF\) unterstützt die meisten Codeausschnitt\-Funktionalität, lesen Sie die Vorlage, die den Ausschnitt einfügen, und aktivieren die speziellen Bearbeitungsmodus. Support erfolgt über die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse.  
  
 Wenn der <xref:Microsoft.VisualStudio.Package.Source> Klasse instanziiert wird, der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse aufgerufen, um erhalten ein <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt \(Beachten Sie, dass die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse gibt immer eine neue <xref:Microsoft.VisualStudio.Package.ExpansionProvider> \-Objekt für jeden <xref:Microsoft.VisualStudio.Package.Source> Objekt\).  
  
 Die MPF unterstützt Erweiterung Funktionen nicht. Eine Erweiterungsfunktion ist eine benannte Funktion, die in einer Ausschnittvorlage eingebettet ist, und gibt einen oder mehrere Werte in einem Feld platziert werden. Die Werte werden zurückgegeben, von der Sprache selbst über eine <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt. Das <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt muss von der Sprachdienst Unterstützung von Funktionen der Erweiterung implementiert werden.  
  
## Bereitstellen von Unterstützung für Codeausschnitte  
 Zum Aktivieren der Unterstützung für Codeausschnitte bereitzustellen oder installieren Sie die Ausschnitte, und geben Sie die bedeutet, dass der Benutzer diese Ausschnitte einfügen. Es gibt drei Schritte zum Aktivieren der Unterstützung für Codeausschnitte aus:  
  
1.  Installieren die Dateien von Codeausschnitten.  
  
2.  Aktivieren Codeausschnitte für Ihren Sprachdienst.  
  
3.  Aufrufen der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt.  
  
### Installieren die Dateien von Codeausschnitten  
 Alle Codeausschnitte für eine Sprache werden in der Regel eine Ausschnittvorlage pro Datei als Vorlagen in XML\-Dateien gespeichert. Ausführliche Informationen über das XML\-Schema für Code\-Ausschnittvorlagen verwendet, finden Sie unter [Schemareferenz für Codeausschnitte](../../ide/code-snippets-schema-reference.md). Jeder Ausschnittvorlage wird mit eine Sprachen\-ID identifiziert. Diese Sprache ID wird in der Registrierung angegeben und ist in der `Language` \-Attribut des \< Code \>\-Tags in der Vorlage.  
  
 Es gibt in der Regel zwei Orte, in dem Codeausschnitt\-Vorlagendateien gespeichert sind: \(1\), in denen Ihre Sprache installiert wurde, und \(2\) in den Ordner des Benutzers. Diese Speicherorte werden der Registrierung hinzugefügt also, die Visual Studio **Codeausschnitt\-Manager** finden Sie die Codeausschnitte. Der Ordner des Benutzers werden vom Benutzer erstellte Codeausschnitte gespeichert.  
  
 Der normale Ordnerstruktur für die installierte Vorlage Ausschnittdateien sieht folgendermaßen aus: *\[InstallRoot\]*\\*\[TestLanguage\]*\\Snippets\\*\[LCID\]*\\Snippets.  
  
 *\[InstallRoot\]* ist der Ordner, die in Ihrer Sprache installiert ist.  
  
 *\[TestLanguage\]* ist der Name der Sprache als einen Ordnernamen ein.  
  
 *\[LCID\]* die Gebietsschema\-ID. Dies ist wie lokalisierte Versionen Ausschnitte gespeichert werden. Die Gebietsschema\-ID für Englisch ist beispielsweise 1033, also *\[LCID\]* durch 1033 ersetzt wird.  
  
 Eine weitere Datei muss angegeben werden, und eine Indexdatei, die in der Regel aufgerufen, SnippetsIndex.xml oder ExpansionsIndex.xml \(Sie können jeden gültigen Dateinamen mit der XML verwenden\). Diese Datei befindet sich in der Regel in der *\[InstallRoot\]*\\*\[TestLanguage\]* Ordner und gibt den genauen Speicherort der Ordner "Snippets" als auch die Sprach\-ID und der GUID des Sprachdiensts, der die Codeausschnitte verwendet. Der genaue Pfad der Indexdatei wird in der Registrierung abgelegt, wie weiter unten in "Installieren der Registrierungseinträge" beschrieben. Hier ist ein Beispiel einer SnippetsIndex.xml\-Datei:  
  
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
  
 Das \< Sprache \>\-Tag gibt die Sprachen\-ID \(die `Lang` Attribut\) und der GUID des Sprachdiensts.  
  
 In diesem Beispiel wird davon ausgegangen, dass Sie Ihre Sprachdienst im Visual Studio\-Installationsordner installiert haben. Der % LCID % wird durch das aktuelle Gebietsschema\-ID des Benutzers ersetzt. Mehrere \< SnippetDir \>\-Tags können hinzugefügt werden, eine für jedes anderen Verzeichnis und Gebietsschema. Darüber hinaus kann Codeausschnittordner Unterordner enthalten, von die jedes in der Indexdatei identifiziert wird, die in einem \< SnippetDir \>\-Tag eingebettet ist mit dem Tag \< SnippetSubDir \>.  
  
 Benutzer können auch eigene Ausschnitte für Ihre Sprache erstellen. Diese werden in der Regel gespeichert im Ordner "Einstellungen" des Benutzers, z. B. *\[TestDocs\]*\\Code Snippets\\*\[TestLanguage\]*\\Test Codeausschnitte, wobei *\[TestDocs\]* ist der Speicherort des Ordners "Einstellungen" des Benutzers für Visual Studio.  
  
 Die folgenden Ersetzungselemente können in dem Pfad gespeichert, die im \< DirPath \>\-Tag in der Indexdatei platziert werden.  
  
|Element|Beschreibung|  
|-------------|------------------|  
|% LCID %|Gebietsschema\-ID.|  
|% Installroot%|Installation\-Stammordner für Visual Studio, z. B. C:\\Program Files\\Microsoft Visual Studio 8.|  
|% ProjDir|Dieser Ordner enthält das aktuelle Projekt.|  
|% ProjItem|Dieser Ordner enthält das aktuelle Projektelement.|  
|% TestDocs|Ordner in den Ordner des Benutzers Einstellungen, z. B. C:\\Documents und Einstellungen\\*\[Benutzername\]*\\My Documents\\Visual Studio\\8.|  
  
### Aktivieren Codeausschnitte für Ihren Sprachdienst  
 Sie können Codeausschnitte für Ihren Sprachdienst aktivieren, durch Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> \-Attribut auf das VSPackage \(finden Sie unter [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md) Details\). Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> und <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> Parameter sind optional, aber Sie sollten berücksichtigen die `SearchPaths` benannter Parameter, um darüber zu informieren die **Codeausschnitt\-Manager** den Speicherort der Ausschnitte.  
  
 Im folgenden finden ein Beispiel für die Verwendung dieses Attributs:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### Aufrufen des Anbieters der Erweiterung  
 Der Sprachdienst steuert das Einfügen von alle Codeausschnitte sowie die Möglichkeit, die aufgerufen wird, einfügen.  
  
## Aufrufen des Anbieters der Erweiterung für Codeausschnitte  
 Es gibt zwei Möglichkeiten zum Aufrufen des Erweiterung Anbieters: mithilfe eines Menübefehls oder mithilfe einer Verknüpfung aus einem Vervollständigungsliste.  
  
### Einfügen eines Codeausschnitts mithilfe eines Menübefehls  
 Um einen Befehl verwenden, um den Ausschnitt\-Browser anzuzeigen, fügen Sie einen Menübefehl hinzu, und rufen Sie dann die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Schnittstelle als Antwort auf diesen Menübefehl.  
  
1.  Fügen Sie einen Befehl und eine Schaltfläche zu Ihrer VSCT\-Datei. Finden Sie Anweisungen zur Vorgehensweise im [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio\-Paketvorlage](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse, und überschreiben die <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> Methode, um Unterstützung für den neuen Menübefehl anzugeben. In diesem Beispiel ermöglicht immer den Menübefehl.  
  
    ```c#  
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
  
3.  Überschreiben der <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.ViewFilter> \-Klasse der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt, und rufen die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode für dieses Objekt.  
  
    ```c#  
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
  
     Die folgenden Methoden in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse werden von Visual Studio in der angegebenen Reihenfolge aufgerufen, bei der Sie den Ausschnitt einfügen:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Nachdem die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> Methode aufgerufen wird, wird der Codeausschnitt eingefügt wurde und die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt befindet sich in einem speziellen Bearbeitungsmodus zum Ändern eines Ausschnitts, das soeben eingefügt wurde.  
  
### Einfügen eines Codeausschnitts mithilfe einer Verknüpfung  
 Implementierung einer Verknüpfung aus einem Vervollständigungsliste ist wesentlich komplexer als die Implementierung eines Menübefehls. Sie müssen zuerst die IntelliSense\-Vervollständigungsliste Word ausschnittsverknüpfungen hinzufügen. Dann müssen Sie erkennen, wenn nach Abschluss des Vorgangs eine Abkürzungsnamen des Ausschnitts eingefügt wurde. Abschließend müssen Sie den Ausschnitt Titel und den Pfad mithilfe von Abkürzungsnamen erhalten und übergeben Sie diese Informationen an die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Methode.  
  
 Um die Word\-Vervollständigungsliste ausschnittsverknüpfungen hinzuzufügen, fügen sie Sie dem <xref:Microsoft.VisualStudio.Package.Declarations> \-Objekt in die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse. Sie müssen sicherstellen, dass Sie die Verknüpfung als ein Codeausschnitt identifizieren können. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte \(Legacy\-Implementierung\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Sie können erkennen, dass das Einfügen der Verknüpfung des Code\-Ausschnitt in die <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> Methode der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Da die Quelldatei den Namen des Ausschnitts bereits eingefügt wurden, muss es entfernt werden, wenn die Erweiterung eingefügt wird. Die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode nimmt ein SPAN\-Tag, das der Einfügemarke für den Codeausschnitt beschreibt, wenn die Spanne der gesamte Ausschnitt\-Name in der Quelldatei enthält, wird dieser Name von Ausschnitt ersetzt.  
  
 Hier ist eine Version von einer <xref:Microsoft.VisualStudio.Package.Declarations> \-Klasse, die Verknüpfung Namen einfügen von Codeausschnitten behandelt. Andere Methoden in der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse aus Gründen der Übersichtlichkeit weggelassen wurden. Beachten Sie, die der Konstruktor dieser Klasse akzeptiert ein <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt. Dies kann mit Ihrer Version des übergeben werden die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt \(z. B. die Implementierung von der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse dauern die <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt in seinem Konstruktor, und übergeben Sie das Objekt auf Ihrer `TestDeclarations` Klassenkonstruktor\).  
  
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
  
 Wenn der Sprachdienst den Namen erhält, ruft er die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> Methode, um den Dateinamen und Code Ausschnitt Titel abzurufen. Der Sprachdienst ruft dann die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse, um den Codeausschnitt einfügen. Die folgenden Methoden werden von Visual Studio aufgerufen, in der angegebenen Reihenfolge in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse während des Prozesses, der den Ausschnitt eingefügt:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Weitere Informationen zum Abrufen einer Liste der installierten Codeausschnitte für Ihren Sprachdienst, finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte \(Legacy\-Implementierung\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## Implementierung der ExpansionFunction\-Klasse  
 Eine Erweiterungsfunktion ist eine benannte Funktion, die in einer Ausschnittvorlage eingebettet ist, und gibt einen oder mehrere Werte in einem Feld platziert werden. Um Funktionen der Erweiterung in Ihrem Sprachdienst zu unterstützen, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> \-Klasse und Implementieren der <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> Methode. Dann müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> \-Klasse eine neue Instanz der\-Version zurückgegeben der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse für jede Erweiterungsfunktion, die Sie unterstützen. Wenn Sie eine Liste der möglichen Werte aus einer Erweiterungsfunktion unterstützen, müssen Sie auch überschreiben die <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse, um eine Liste der Werte zurück.  
  
 Eine Erweiterungsfunktion, die Argumente akzeptiert, oder muss Zugriff auf andere Felder sollten nicht bearbeitbares Feld zugeordnet werden, wie die Erweiterung Anbieter nicht vollständig bis zu dem Zeitpunkt initialisiert werden kann, wenn die Erweiterungsfunktion aufgerufen wird. Die Erweiterungsfunktion ist daher nicht den Wert der Argumente oder ein anderes Feld zu erhalten.  
  
### Beispiel  
 Hier ist ein Beispiel für eine einfache Erweiterung\-Funktion wie bezeichnete `GetName` implementiert werden. Diese Erweiterungsfunktion Fügt eine Anzahl an einen Namen für die Basisklasse jedes Mal die Erweiterungsfunktion instanziiert wird \(Dies entspricht jedem den zugehörige Code\-Ausschnitt wird eingefügt\).  
  
```c#  
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
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Codeausschnitte](../../ide/code-snippets.md)   
 [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte \(Legacy\-Implementierung\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
---
title: "Unterstützung für Codeausschnitte in einen Legacy-Sprachdienst | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0089e5a8bf85ba352788767c821d95f41ca60eec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Unterstützung für Codeausschnitte in einen Legacy-Sprachdienst
Ein Codeausschnitt ist ein Teil des Codes, der in die Quelldatei eingefügt wird. Des Codeausschnitts selbst finden Sie eine XML-basierte Vorlage mit einem Satz von Feldern. Diese Felder werden hervorgehoben, nachdem der Codeausschnitt eingefügt und kann haben unterschiedliche Werte je nach Zusammenhang, in der der Codeausschnitt eingefügt wird. Sofort, nachdem der Codeausschnitt eingefügt wird, kann der Sprachdienst den Ausschnitt formatieren.  
  
 Der Codeausschnitt wird in einer speziellen Bearbeitungsmodus eingefügt, die die Felder des Ausschnitts, um mit der TAB-Taste navigiert werden können. Die Felder können IntelliSense-Stil Dropdown-Menüs unterstützen. Der Benutzer führt einen Commit für den Ausschnitt an der Quelldatei Geben Sie die EINGABETASTE oder ESC-Taste. Weitere Informationen zu Codeausschnitten finden Sie unter [Codeausschnitte](../../ide/code-snippets.md).  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework-Unterstützung für Codeausschnitte  
 Des managed Package Framework (MPF) unterstützt die meisten Funktionen für den Ausschnitt, lesen Sie die Vorlage, die den Ausschnitt eingefügt, und aktivieren die speziellen Bearbeitungsmodus. Unterstützung erfolgt über die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse.  
  
 Wenn der <xref:Microsoft.VisualStudio.Package.Source> Klasse instanziiert wird, der <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse aufgerufen, um erhalten eine <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt (Beachten Sie, dass die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse gibt immer eine neue <xref:Microsoft.VisualStudio.Package.ExpansionProvider> -Objekt für jedes <xref:Microsoft.VisualStudio.Package.Source> -Objekt).  
  
 Das MPF unterstützt Erweiterung Funktionen nicht. Eine Erweiterungsfunktion handelt es sich um eine benannte Funktion, die in einem Ausschnittvorlage eingebettet ist, und gibt einen oder mehrere Werte in einem Feld platziert werden soll. Die Werte werden von der Sprache zurückgegeben-Diensts über einen <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt. Die <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt muss von der Sprachdienst zur Unterstützung der Erweiterung Funktionen implementiert werden.  
  
## <a name="providing-support-for-code-snippets"></a>Bereitstellen von Unterstützung für Codeausschnitte  
 Um Unterstützung für Codeausschnitte zu aktivieren, müssen von Ihnen bereitgestellte oder installieren Sie die Ausschnitte, und Sie müssen die notwendigen Mittel zum Benutzer diese Ausschnitte Einfügen bereitstellen. Es gibt drei Schritte zur Aktivierung von Unterstützung für Codeausschnitte:  
  
1.  Installieren die Snippet-Dateien.  
  
2.  Aktivieren Codeausschnitte für Ihren Sprachdienst.  
  
3.  Aufrufen der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt.  
  
### <a name="installing-the-snippet-files"></a>Installieren die Snippet-Dateien  
 Alle Codeausschnitte für eine Sprache werden in der Regel eine Ausschnittvorlage pro Datei als Vorlagen in XML-Dateien gespeichert. Ausführliche Informationen zu den XML-Schema für Code Snippet Vorlagen verwendet, finden Sie unter [Schemareferenz für Codeausschnitte](../../ide/code-snippets-schema-reference.md). Jede Ausschnittvorlage wird mit einer Sprachen-ID identifiziert. Diese Sprache-ID in der Registrierung angegeben ist und abgelegt wird die `Language` Attribut des der \<Code > Tag in der Vorlage.  
  
 Es gibt in der Regel zwei Orte, auf die Snippet-Vorlagendateien gespeichert sind: (1), in denen Ihre Sprache installiert wurde, und (2) in den Ordner des Benutzers. Diese Speicherorte werden zur Registrierung hinzugefügt daher, Visual Studio **Codeausschnitt-Manager** Ausschnitte finden. Der Ordner des Benutzers ist, wo die Ausschnitte, die vom Benutzer erstellten gespeichert werden.  
  
 Das typische Ordner Layout für die Vorlagendateien installierten Ausschnitt sieht wie folgt aus: *[InstallRoot]*\\*[TestLanguage]*\Snippets\\*[LCID]*\Snippets.  
  
 *[InstallRoot]*  ist der Ordner, die in Ihrer Sprache installiert ist.  
  
 *[TestLanguage]*  ist der Name der Sprache als einen Ordnernamen ein.  
  
 *[LCID]*  die Gebietsschema-ID. Hierbei handelt es sich um Ausschnitte wie lokalisierte Versionen gespeichert werden. Z. B. die Gebietsschema-ID für Englisch gleich 1033 ist, also *[LCID]* durch 1033 ersetzt wird.  
  
 Eine weitere Datei muss angegeben werden, und eine Indexdatei, die in der Regel aufgerufen SnippetsIndex.xml oder ExpansionsIndex.xml (Sie können jeden gültigen Dateinamen Endziffern XML verwenden). Diese Datei befindet sich in der Regel in der *[InstallRoot]*\\*[TestLanguage]* Ordner und gibt den genauen Speicherort der Ausschnitte Ordner als auch die Sprach-ID und die GUID der Sprache Dienst, der die Ausschnitte verwendet. Der genaue Pfad, der die Indexdatei ist in der Registrierung belasten, da weiter unten in "Installieren der Registrierungseinträge" beschrieben. Hier ist ein Beispiel einer SnippetsIndex.xml-Datei ein:  
  
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
  
 Die \<Sprache >-Tag gibt die Sprach-ID (die `Lang` Attribut) und die GUID des Sprachdiensts.  
  
 In diesem Beispiel wird davon ausgegangen, dass Sie Ihre Sprachdienst in Visual Studio-Installationsordner installiert haben. Der % LCID % wird durch das aktuelle Gebietsschema-ID des Benutzers ersetzt. Mehrere \<SnippetDir > Tags hinzugefügt werden können, eine für jeden anderen Verzeichnis und Gebietsschema. Darüber hinaus darf ein ausschnittordners Unterordner, von denen jede wird in die Indexdatei mit identifiziert die \<SnippetSubDir >-Tag, das in eingebettet ist eine \<SnippetDir > Tag.  
  
 Benutzer können auch eigene Ausschnitte für Ihre Sprache erstellen. Diese werden in der Regel gespeichert im Ordner "Einstellungen" des Benutzers, z. B. *[TestDocs]*\Code Ausschnitte\\*[TestLanguage]*\Test Codeausschnitte, wobei *[TestDocs]* ist der Speicherort des Ordners für die Einstellungen des Benutzers für Visual Studio.  
  
 Die folgenden Ersetzungselemente platziert werden können, in dem Pfad gespeichert, der \<DirPath >-Tag in der Indexdatei.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|% LCID %|Gebietsschema-ID.|  
|"% InstallRoot"|Stamminstallationsordners für Visual Studio, z. B. C:\Program Files\Microsoft Visual Studio 8.|  
|"% ProjDir"|Dieser Ordner enthält das aktuelle Projekt.|  
|"% ProjItem"|Dieser Ordner enthält das aktuelle Projektelement.|  
|"% TestDocs"|Ordner "Einstellungen" des Benutzers, z. B. C:\Documents and Settings\\*[Username]*\My Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Aktivieren Codeausschnitte für Ihre-Sprachdienst  
 Können Sie Codeausschnitte für Ihre Sprachdienst aktivieren, durch Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> -Attribut auf das VSPackage (finden Sie unter [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) Einzelheiten). Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> und <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> Parameter sind optional, aber Sie sollten berücksichtigen die `SearchPaths` benannter Parameter um informiert die **Codeausschnitt-Manager** des Speicherorts der Ausschnitte.  
  
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
  
### <a name="calling-the-expansion-provider"></a>Aufrufen des Anbieters der Erweiterung  
 Der Sprachdienst steuert das Einfügen von alle Codeausschnitte sowie die Möglichkeit, Einfügung aufgerufen wird.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Aufrufen des Anbieters der Erweiterung für Codeausschnitte  
 Es gibt zwei Möglichkeiten zum Aufrufen des Anbieters der Erweiterung: mithilfe eines Menübefehls oder mithilfe einer Verknüpfung aus einem Vervollständigungsliste.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Einfügen eines Codeausschnitts mithilfe eines Menübefehls  
 Um einen Menübefehl verwenden, um den Ausschnitt Browser anzuzeigen, fügen Sie einen Menübefehl hinzu, und rufen Sie anschließend die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Schnittstelle als Antwort auf diesem Menübefehl.  
  
1.  Fügen Sie einen Befehl und eine Schaltfläche in der VSCT-Datei an. Finden Sie Anleitungen, um auf diese Weise im [erstellen eine Erweiterung mit einem Menübefehl](../../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Leiten Sie eine Klasse aus der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse, und überschreiben die <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> Methode, um Unterstützung für den neuen Menübefehl anzugeben. In diesem Beispiel ermöglicht immer den Menübefehl aus.  
  
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
  
3.  Überschreiben der <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> Methode in der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse zum Abrufen der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt, und rufen die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode für dieses Objekt.  
  
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
  
     Nach der <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> -Methode aufgerufen wird, wurde der Codeausschnitt eingefügt und die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt befindet sich in einem speziellen Bearbeitungsmodus zum Ändern eines Ausschnitts, das soeben eingefügt wurde.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Einfügen eines Codeausschnitts mithilfe einer Verknüpfung  
 Die Implementierung einer Verknüpfung aus einem Vervollständigungsliste ist deutlich komplizierter als das Implementieren eines Menübefehls. Sie müssen zuerst die IntelliSense-Vervollständigungsliste für Word-ausschnittsverknüpfungen hinzufügen. Dann müssen Sie erkennen, wenn aufgrund der Beendigung einer Abkürzungsnamen des Ausschnitts eingefügt wurde. Schließlich müssen Sie den Ausschnitt Titel und den Pfad, die mithilfe von Abkürzungsnamen zu erhalten und übergeben Sie diese Informationen, um die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Methode.  
  
 Um die Vervollständigungsliste für Word-ausschnittsverknüpfungen hinzugefügt haben, fügen Sie damit die <xref:Microsoft.VisualStudio.Package.Declarations> Objekt in Ihrer <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse. Sie müssen sicherstellen, dass Sie die Verknüpfung als Namen des Ausschnitts ein identifizieren können. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacy-Implementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Sie können erkennen, dass das Einfügen von Code Snippet Verknüpfung der <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> Methode der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Da in der Quelldatei bereits den Namen des Ausschnitts eingefügt wurde, muss er entfernt werden, wenn die Erweiterung eingefügt wird. Die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode akzeptiert eine Spanne, die der Einfügemarke für den Ausschnitt beschreibt; Wenn die Spanne der gesamte Ausschnitt-Name in der Quelldatei enthält, wird dieser Name durch den Ausschnitt ersetzt.  
  
 Hier ist eine Version von einem <xref:Microsoft.VisualStudio.Package.Declarations> -Klasse, die Ausschnitt einfügen, die eine Verknüpfung benannt behandelt. Andere Methoden in der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse aus Gründen der Übersichtlichkeit weggelassen wurden. Beachten Sie, die der Konstruktor dieser Klasse benötigt ein <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt. Dies kann von Ihrer Version des übergeben werden der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt (z. B. die Implementierung von der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse dauern die <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt in seinem Konstruktor, und übergeben Sie das Objekt auf Ihre `TestDeclarations` Klassenkonstruktor).  
  
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
  
 Wenn der Sprachdienst Abkürzungsnamen abruft, ruft er die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> Methode, um den Titel der Ausschnitt Dateinamen- und Code abzurufen. Der Sprachdienst ruft dann die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse, um den Codeausschnitt einfügen. Die folgenden Methoden werden von Visual Studio aufgerufen, in der angegebenen Reihenfolge in der <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse während des Prozesses, der den Ausschnitt eingefügt:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Weitere Informationen zum Abrufen einer Liste der installierten Codeausschnitte für Ihren Sprachdienst finden Sie unter [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacy-Implementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>Implementieren die ExpansionFunction-Klasse  
 Eine Erweiterungsfunktion handelt es sich um eine benannte Funktion, die in einem Ausschnittvorlage eingebettet ist, und gibt einen oder mehrere Werte in einem Feld platziert werden soll. Um die Funktionen der Erweiterung in der Sprachdienst zu unterstützen, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse und Implementieren der <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> Methode. Müssen Sie überschreiben, klicken Sie dann die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse eine neue Instanz Ihrer Version des zurückzugebenden der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse für jede Erweiterungsfunktion, die Sie unterstützen. Wenn Sie eine Liste der möglichen Werte aus einer Erweiterungsfunktion unterstützen, müssen Sie auch überschreiben die <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> Methode in der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse, um eine Liste dieser Werte zurückzugeben.  
  
 Eine Erweiterungsfunktion, die Argumente akzeptiert, oder den Zugriff auf andere Felder muss sollte nicht mit ein bearbeitbares Feld verknüpft sein, wie der Erweiterung Anbieter nicht vollständig von der Zeit initialisiert werden kann, die die Erweiterungsfunktion aufgerufen wird. Daher kann die Erweiterungsfunktion nicht zum Abrufen des Werts der Argumente oder ein anderes Feld.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein Beispiel für eine einfache Erweiterung-Funktion wie aufgerufen `GetName` implementiert werden könnten. Diese Erweiterungsfunktion Fügt eine Anzahl an eine Basisklassennamen jedes Mal die Erweiterungsfunktion instanziiert wird (welcher entspricht jedem den zugehörigen Codeausschnitt eingefügt wird).  
  
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
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Codeausschnitte](../../ide/code-snippets.md)   
 [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
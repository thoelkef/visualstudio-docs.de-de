---
title: Implementieren von einem Legacysprachdienst 2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8158a8eaf4b0ee85858cc81e93fbb7e4fa0b9f8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893772"
---
# <a name="implementing-a-legacy-language-service"></a>Implementieren eines Legacysprachdiensts
Um einen Sprachdienst mithilfe des managed Package Frameworks (MPF) zu implementieren, müssen Sie leiten eine Klasse von der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und implementieren Sie die folgenden abstrakten Methoden und Eigenschaften:  
  
- Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> -Methode  
  
- Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>-Methode  
  
- Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode  
  
- Die <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>-Eigenschaft.  
  
  Finden Sie unter den entsprechenden Abschnitten weiter unten Weitere Informationen zum Implementieren dieser Methoden und Eigenschaften ein.  
  
  Um zusätzliche Funktionen zu unterstützen, möglicherweise der Sprachdienst Ableiten einer Klasse von einer der die MPF-Language-Dienstklassen; beispielsweise, um zusätzliche Menübefehle zu unterstützen, muss, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse, und überschreiben Sie mehrere des Befehls im Umgang mit Methoden (finden Sie unter <xref:Microsoft.VisualStudio.Package.ViewFilter> Einzelheiten). Die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse bietet eine Reihe von Methoden, die aufgerufen werden, um neue Instanzen verschiedener Klassen zu erstellen, und Sie überschreiben die entsprechenden Erstellungsmethode, um eine Instanz der Klasse bereitstellen. Beispielsweise müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse die Rückgabe einer Instanz Ihrer eigenen <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse. Finden Sie im Abschnitt "Instanziieren benutzerdefinierte Klassen" Weitere Details.  
  
  Der Sprachdienst kann auch eigene Symbole, angeben, die an vielen Stellen verwendet werden. Z. B. wenn eine IntelliSense-Vervollständigungsliste angezeigt wird, kann jedes Element in der Liste ein Symbol zugeordnet, markieren das Element als Methode, Klasse, Namespace, Eigenschaft oder was für Ihre Sprache nötig ist. Diese Symbole werden verwendet, in allen IntelliSense-Listen, die **Navigationsleiste**, und klicken Sie in der **Fehlerliste** Aufgabenfenster. Finden Sie unter "Language Service Images" weiter unten im Abschnitt Details.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences-Methode  
 Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode gibt immer die gleiche Instanz von einem <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Sie können die Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse, wenn Sie zusätzlichen Einstellungen für den Sprachdienst nicht erforderlich ist. Die MPF-Language-Dienstklassen davon aus, das Vorhandensein von mindestens die Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine typische Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode. Dieses Beispiel verwendet die Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>GetScanner-Methode  
 Diese Methode gibt eine Instanz zurück. ein <xref:Microsoft.VisualStudio.Package.IScanner> -Objekt, das eine zeilenorientierte Parser oder Scanner, die zum Abrufen von Token und deren Typen und Trigger verwendet, implementiert. Diese Überprüfung wird verwendet, der <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse für die farbliche Kennzeichnung, obwohl die Überprüfung auch für das Abrufen von Tokentypen und Trigger als Vorbereitung auf eine komplexere Analysevorgang verwendet werden kann. Sie müssen angeben, dass die Klasse, implementiert die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle, und Sie müssen alle Methoden implementieren, auf die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine typische Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode. Die `TestScanner` -Klasse implementiert die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle (nicht dargestellt).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>ParseSource-Methode  
 Analysiert die Quelldatei, die basierend auf einer Reihe unterschiedlicher Ursachen. Diese Methode erhält eine <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, das beschreibt, was von einem bestimmten Analysevorgang erwartet wird. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode aufruft, einen komplexeren Parser, der token-Funktion und den Bereich bestimmt. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode wird bei der Unterstützung für IntelliSense-Vorgänge sowie zugehörige Klammern verwendet. Auch wenn Sie keine solche erweiterte Vorgänge unterstützen, Sie immer noch müssen zurückkehren, eine gültige <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt und die erfordert, dass Sie eine Klasse erstellen, die implementiert die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Schnittstelle, und alle Methoden auf diese Schnittstelle implementieren. Sie können alle Methoden null-Werte zurückgeben, aber die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt selbst muss sich nicht auf einen null-Wert.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine minimale Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode und die <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Klasse ausreichend, um den Sprachdienst zu kompilieren und ohne Unterstützung der erweiterten Funktionen tatsächlich funktionieren können.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Name-Eigenschaft  
 Diese Eigenschaft gibt den Namen des Sprachdiensts zurück. Dies muss den gleichen Namen, wenn der Sprachdienst registriert wurde. Dieser Name wird verwendet, in einer Reihe von Orten, von denen die bekannteste ist die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse, die der Name, in denen verwendet wird auf die Registrierung zuzugreifen. Der von dieser Eigenschaft zurückgegebene Name muss nicht lokalisiert werden, da es für den Registrierungseintrag und Schlüsselnamen in der Registrierung verwendet wird.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine mögliche Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Eigenschaft. Beachten Sie, dass hier den Namen der fest programmierte: der tatsächliche Name sollte aus einer Ressourcendatei abgerufen werden, damit sie verwendet werden kann, registrieren Sie einen Sprachdienst (finden Sie unter [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>Instanziieren benutzerdefinierte Klassen  
 Die folgenden Methoden in den angegebenen Klassen können überschrieben werden, um Ihre eigenen Versionen der einzelnen Klassen Instanzen bereitzustellen.  
  
### <a name="in-the-languageservice-class"></a>In der LanguageService-Klasse  
  
|Methode|Zurückgegebene Klasse|Beschreibung|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Um benutzerdefinierte Ergänzungen der Textansicht zu unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Zur Unterstützung von benutzerdefinierten Dokumenteigenschaften.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Zur Unterstützung der **Navigationsleiste**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Unterstützung von Funktionen in Codeausschnittvorlagen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Codeausschnitte unterstützt (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Zur Unterstützung der Anpassung der <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Zur Unterstützung von Formatierung Quellcode angeben Kommentarzeichen und Anpassen von Methodensignaturen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Um zusätzliche Menübefehle zu unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Zur Unterstützung der syntaxhervorhebung (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Um den Zugriff auf die spracheinstellungen zu unterstützen. Diese Methode muss implementiert werden, aber es kann eine Instanz der Basisklasse zurückgegeben.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Um einen Parser, der zum Identifizieren von Tokentypen in einer Zeile bereitzustellen. Diese Methode implementiert werden muss und <xref:Microsoft.VisualStudio.Package.IScanner> abgeleitet werden müssen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Um einen Parser, der zum Identifizieren von Funktionen und der Gültigkeitsbereich für eine gesamte Quelldatei bereitzustellen. Diese Methode muss implementiert werden und muss eine Instanz Ihrer Version von Zurückgeben der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse. Wenn Sie unterstützen möchten syntaxhervorhebung ist (erfordert die <xref:Microsoft.VisualStudio.Package.IScanner> zurückgegeben, die vom Parser die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode), möglich "nothing" in dieser Methode als Rückgabewert eine Version von der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, deren Methoden, die alle null-Werte zurück.|  
  
### <a name="in-the-source-class"></a>In der Quellklasse  
  
|Methode|Zurückgegebene Klasse|Beschreibung|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Zum Anpassen der Anzeige von IntelliSense-Vervollständigungslisten (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Für die Unterstützung der Marker in der Fehlerliste Aufgabenliste; insbesondere Unterstützung für die Datei zu öffnen, und springen zu der Zeile, die den Fehler verursacht hat.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Zum Anpassen der Anzeige des QuickInfo-Tipps für IntelliSense-Parameter.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Für die Unterstützung von Kommentieren von Code.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Für das Sammeln von Informationen während des Analysevorgangs.|  
  
### <a name="in-the-authoringscope-class"></a>In der AuthoringScope-Klasse  
  
|Methode|Zurückgegebene Klasse|Beschreibung|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Enthält eine Liste der Deklarationen wie z. B. Membern oder Typen. Diese Methode muss implementiert werden, aber es kann einen null-Wert zurückgeben. Wenn diese Methode ein gültiges Objekt zurückgibt, muss das Objekt eine Instanz von Ihrer Version von der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Enthält eine Liste von Methodensignaturen für einen angegebenen Kontext. Diese Methode muss implementiert werden, aber es kann einen null-Wert zurückgeben. Wenn diese Methode ein gültiges Objekt zurückgibt, muss das Objekt eine Instanz von Ihrer Version von der <xref:Microsoft.VisualStudio.Package.Methods> Klasse.|  
  
## <a name="language-service-images"></a>Bereitstellen von Images Language  
 Überschreiben, um eine Liste der Symbole in der gesamten der Sprachdienst verwendet werden zu ermöglichen, die <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und Zurückgeben einer <xref:System.Windows.Forms.ImageList> , die die Symbole enthält. Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse lädt einen Standardsatz von Symbolen. Da Sie den genauen Bildindex an diesen Orten, die Symbole benötigen angeben, ist wie Sie Ihre eigenen Bildliste anordnen völlig Ihnen überlassen.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Images, die In IntelliSense-Vervollständigungslisten verwendet werden.  
 Für IntelliSense-Vervollständigungslisten, den Index des Bildes angegeben ist, für jedes Element in der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Methode der <xref:Microsoft.VisualStudio.Package.Declarations> -Klasse, die Sie überschreiben müssen, wenn Sie einen Image-Index angeben möchten. Der Rückgabewert der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Methode ist ein Index in der Bildliste angegeben die <xref:Microsoft.VisualStudio.Package.CompletionSet> Klassenkonstruktor und, dieselbe Bildliste von zurückgegeben wird der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse (Sie können Ändern der Bildliste an, Verwenden Sie für die <xref:Microsoft.VisualStudio.Package.CompletionSet> , wenn Sie außer Kraft setzen der <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.Source> Klasse, um ein anderes Bildliste angeben).  
  
### <a name="images-used-in-the-navigation-bar"></a>Images, die in der Navigationsleiste verwendet werden.  
 Die **Navigationsleiste** Zeigt Listen von Typen und Membern an und wird verwendet, für eine schnelle Navigation Symbole angezeigt werden kann. Diese Symbole werden abgerufen, von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und kann nicht überschrieben werden, speziell für die **Navigationsleiste**. Die Indizes, die für jedes Element in den Kombinationsfeldern verwendet angegeben sind, wenn die Listen, die die Kombinationsfeldern darstellt, in aufgefüllt sind der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse (finden Sie unter [Unterstützung für die Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Diese Images Indizes sind irgendwie von dem Parser abgerufen, in der Regel durch Ihre Version von der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Wie die Indizes abgerufen werden, ist völlig Ihnen überlassen.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Images, die in der Fehlerliste (Fenster) Aufgabe verwendet werden.  
 Wenn die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser (finden Sie unter [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) ein Fehler auftritt, und übergeben Sie diesen Fehler zu der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse, der Fehler wird gemeldet, in der  **Fehlerliste** Aufgabenfenster. Ein Symbol kann mit jedes Element, das im Fenster Aufgabenliste angezeigt wird und das Symbol stammt dieselbe Bildliste zurückgegeben, die von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Das Standardverhalten der die MPF-Klassen werden nicht auf ein Bild mit der Fehlermeldung angezeigt. Sie können dieses Verhalten jedoch überschreiben, durch Ableiten einer Klasse von der <xref:Microsoft.VisualStudio.Package.Source> und überschreiben die <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> Methode. In dieser Methode erstellen Sie ein neues <xref:Microsoft.VisualStudio.Package.DocumentTask> Objekt. Bevor das Objekt zurückgegeben wird, können Sie die <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> Eigenschaft für die <xref:Microsoft.VisualStudio.Package.DocumentTask> Objekt, das den Index des Bildes festgelegt. Dies würde in etwa wie im folgenden Beispiel aussehen. Beachten Sie, dass `TestIconImageIndex` ist eine Enumeration, die alle Symbole aufgeführt und ist spezifisch für dieses Beispiel. Sie müssen möglicherweise eine andere Art der Symbole in den Sprachdienst zu identifizieren.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TaskPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>Der standardmäßigen Bildliste für einen Sprachdienst  
 Die standardmäßigen Bildliste, die mit die MPF Language Service Basisklassen angegeben, enthält eine Reihe von Symbolen, die häufiger Sprachelemente zugeordnet. Der größte Teil dieser Symbole sind in Gruppen von sechs Varianten, die für die Access-Konzepte der öffentlich, intern, geschützt, privat, Freund und Tastenkombinationen angeordnet. Beispielsweise haben Sie eine Methode, je nachdem, ob es öffentlich, geschützt oder privat mit unterschiedlichen Symbolen dargestellt.  
  
 Die folgende Enumeration typische Namen für jeden Symbolsatz gibt an, und gibt an, der zugehörige Index. Beispielsweise basierend auf der Enumeration, Sie können angeben der Bildindex für eine geschützte Methode als `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Sie können die Namen in dieser Enumeration wie gewünscht ändern.  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
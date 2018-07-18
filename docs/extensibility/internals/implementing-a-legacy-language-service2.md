---
title: Implementieren eine Vorgängerversion Sprache Service2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d54572bc3b105af01ed42b01a27f363da80d58de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134990"
---
# <a name="implementing-a-legacy-language-service"></a>Implementieren einen Sprachdienst Legacy
Um einen Sprachdienst mithilfe des managed Package Frameworks (MPF) zu implementieren, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und implementieren Sie die folgenden abstrakten Methoden und Eigenschaften:  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>-Methode  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>-Methode  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>-Eigenschaft.  
  
 Finden Sie unter den entsprechenden Abschnitten finden Sie weitere Details zum Implementieren von diesen Methoden und Eigenschaften ein.  
  
 Um zusätzliche Funktionen zu unterstützen, möglicherweise Ihre Sprachdienst Ableiten einer Klasse von einer der die MPF-Language-Dienstklassen; Angenommen, um zusätzliche Menübefehle zu unterstützen, muss, leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse, und überschreiben Sie einige der Methoden der befehlsbehandelung (finden Sie unter <xref:Microsoft.VisualStudio.Package.ViewFilter> Einzelheiten). Die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse bietet eine Reihe von Methoden, die aufgerufen werden, um neue Instanzen verschiedener Klassen zu erstellen und Sie überschreiben die entsprechenden Erstellungsmethode, um eine Instanz einer Klasse anzugeben. Beispielsweise müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse, um eine eigene Instanz zurückzugeben <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse. Finden Sie im Abschnitt "Instanziieren benutzerdefinierte Klassen" für weitere Details.  
  
 Der Sprachdienst kann auch eigene Symbole angeben, die in vielen Stellen verwendet werden. Z. B. wenn ein IntelliSense-Vervollständigungsliste angezeigt wird, kann jedes Element in der Liste ein Symbol zugeordnet, markieren das Element als Methode, Klasse, Namespace, Eigenschaft oder was ist erforderlich, die für Ihre Sprache. Diese Symbole werden verwendet, in alle IntelliSense-Listen, die **Navigationsleiste**, und klicken Sie in der **Fehlerliste** Aufgabenfenster. Finden Sie unter "Bereitstellen von Images Language" im Abschnitt unten.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences-Methode  
 Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode gibt immer die gleiche Instanz von einem <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Sie können die Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse, wenn Sie keine zusätzlichen Einstellungen für den Sprachdienst nicht benötigen. Die MPF-Language-Dienstklassen gehen davon aus, das mindestens auf das Vorhandensein Base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine typische Implementierung der der <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode. In diesem Beispiel verwendet die Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
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
 Diese Methode gibt eine Instanz von einem <xref:Microsoft.VisualStudio.Package.IScanner> -Objekt, das einem zeilenorientierten Parser oder Scanner, die zum Abrufen von Token und deren Typen und Trigger verwendet implementiert wird. Dieser Scanner wird verwendet, der <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse für die farbliche Kennzeichnung, obwohl der Scanner auch zum Abrufen von Tokentypen und Triggern als eine Einführung zu einem komplexeren Analysevorgang verwendet werden kann. Sie müssen angeben, dass die implementierende Klasse der <xref:Microsoft.VisualStudio.Package.IScanner> -Schnittstelle, und Sie müssen alle Methoden implementieren, auf die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine typische Implementierung der der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode. Die `TestScanner` -Klasse implementiert die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle (nicht dargestellt).  
  
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
 Analysiert die Quelldatei, die basierend auf einer Reihe von verschiedenen Gründen an. Diese Methode erhält eine <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, das beschreibt, was von einem bestimmten Analysevorgang erwartet wird. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode aufruft, einen komplexeren Parser, der token-Funktionen und Umfang bestimmt. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode wird bei der Unterstützung für IntelliSense-Vorgänge sowie Klammer verwendet. Auch wenn Sie solche erweiterte Vorgänge nicht unterstützt werden, Sie weiterhin müssen zurückgegeben gültige <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt und die erfordert, dass Sie eine Klasse erstellen, die implementiert die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Schnittstelle, und alle Methoden auf diese Schnittstelle implementieren. Sie können null-Werte zurückgeben, von allen Methoden aber die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt selbst darf nicht null-Wert sein.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine minimale Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode und die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse ausreichen, der Sprachdienst zu kompilieren und ohne Unterstützung der tatsächlich keines der erweiterten Funktionen funktionieren.  
  
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
 Diese Eigenschaft gibt den Namen des Sprachdiensts zurück. Diese Angabe muss den gleichen Namen, wenn der Sprachdienst registriert wurde. Dieser Name wird verwendet, in einer Reihe stellen, die bekannteste davon ist die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse, in dem der Name verwendet wird, auf die Registrierung zuzugreifen. Der Name, der von dieser Eigenschaft zurückgegebene muss nicht lokalisiert werden, da sie für den Registrierungseintrag und Schlüsselnamen in der Registrierung verwendet wird.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine mögliche Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Eigenschaft. Beachten Sie, dass hier der Name hartcodiert ist: der tatsächliche Name sollte aus einer Ressourcendatei abgerufen werden, damit sie verwendet werden kann, registrieren Sie einen Sprachdienst (finden Sie unter [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
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
  
## <a name="instantiating-custom-classes"></a>Benutzerdefinierte Instanziieren von Klassen  
 Die folgenden Methoden in den angegebenen Klassen können überschrieben werden, damit Ihre eigenen Versionen der einzelnen Klassen diese Instanzen sind.  
  
### <a name="in-the-languageservice-class"></a>In der LanguageService-Klasse  
  
|Methode|Zurückgegebene Klasse|Beschreibung|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Um benutzerdefinierte Ergänzungen Textansicht zu unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Unterstützung von benutzerdefinierten Dokumenteigenschaften|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Zur Unterstützung der **Navigationsleiste**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Um Funktionen in Code Snippet Vorlagen zu unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Codeausschnitte unterstützt (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Unterstützung der Anpassung von der <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Zur Unterstützung von Formatierung Quellcode Kommentarzeichen angeben und Methodensignaturen anpassen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Um zusätzliche Menübefehle zu unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Zur Unterstützung der syntaxhervorhebung (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Um den Zugriff auf den bevorzugten Sprache zu unterstützen. Diese Methode muss implementiert werden, jedoch kann eine Instanz der Basisklasse zurückgegeben.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Geben Sie einen Parser für die Identifizierung der Tokentypen in einer Zeile verwendet. Diese Methode implementiert werden muss und <xref:Microsoft.VisualStudio.Package.IScanner> abgeleitet werden müssen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Geben Sie einen Parser zum Identifizieren von Funktionen und der Gültigkeitsbereich einer gesamten Quelldatei verwendet. Diese Methode muss implementiert werden und muss eine Instanz Ihrer Version von Zurückgeben der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse. Wenn alle gewünschten syntaxhervorhebung ist (erfordert die <xref:Microsoft.VisualStudio.Package.IScanner> zurückgegeben, die vom Parser die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode), möglich "nothing" in dieser Methode als Rückgabewert eine Version von der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, deren Methoden geben alle null-Werte zurück.|  
  
### <a name="in-the-source-class"></a>In der Quellklasse  
  
|Methode|Zurückgegebene Klasse|Beschreibung|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Zum Anpassen der Anzeige von IntelliSense-Vervollständigungslisten (diese Methode wird in der Regel nicht überschrieben).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Für die Unterstützung der Marker in der Fehlerliste Aufgabenliste; insbesondere Unterstützung für Funktionen jenseits des Öffnen der Datei, und springen zur Zeile, die den Fehler verursacht hat.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Zum Anpassen der Anzeige von QuickInfos IntelliSense-Parameter.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Zur Unterstützung von Kommentieren von Code.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Für das Sammeln von Informationen während der Analysevorgang.|  
  
### <a name="in-the-authoringscope-class"></a>In der AuthoringScope-Klasse  
  
|Methode|Zurückgegebene Klasse|Beschreibung|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Enthält eine Liste der Deklarationen wie Member oder Typen. Diese Methode muss implementiert werden, jedoch kann einen null-Wert zurückgeben. Wenn diese Methode ein gültiges Objekt zurückgibt, muss das Objekt eine Instanz von Ihrer Version von den <xref:Microsoft.VisualStudio.Package.Declarations> Klasse.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Enthält eine Liste der Methodensignaturen für einen angegebenen Kontext. Diese Methode muss implementiert werden, jedoch kann einen null-Wert zurückgeben. Wenn diese Methode ein gültiges Objekt zurückgibt, muss das Objekt eine Instanz von Ihrer Version von den <xref:Microsoft.VisualStudio.Package.Methods> Klasse.|  
  
## <a name="language-service-images"></a>Bereitstellen von Images Sprache  
 Überschreiben, um eine Liste der Symbole in der gesamten Sprachdiensts verwendet werden zu gewährleisten, die <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und Zurückgeben einer <xref:System.Windows.Forms.ImageList> , die die Symbole enthält. Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse lädt eine Reihe von Symbolen. Da Sie den genauen Bildindex an diesen Orten, die Symbole benötigen angeben, ist wie Sie eigene Bildliste anordnen alleine Sie.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>In der IntelliSense-Vervollständigungslisten verwendete Bilder  
 Für IntelliSense-Vervollständigungslisten Bildindex angegeben ist, für jedes Element in der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Methode der <xref:Microsoft.VisualStudio.Package.Declarations> -Klasse, die Sie überschreiben müssen, wenn Sie einen Abbildindex angeben möchten. Ein Rückgabewert der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Methode ist ein Index in die Bildliste für angegebene der <xref:Microsoft.VisualStudio.Package.CompletionSet> Klassenkonstruktor, und dieselbe Bildliste zurückgegeben, aus der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse (Sie können ändern, welche Bildliste Verwenden Sie für die <xref:Microsoft.VisualStudio.Package.CompletionSet> , wenn Sie außer Kraft setzen die <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse, um ein anderes Bildliste angeben).  
  
### <a name="images-used-in-the-navigation-bar"></a>In der Navigationsleiste verwendete Bilder  
 Die **Navigationsleiste** Zeigt Listen von Typen und Membern an und wird verwendet, für die schnelle Navigation Symbole angezeigt werden kann. Diese Symbole erhalten Sie vom der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse und kann nicht überschrieben werden, insbesondere für die **Navigationsleiste**. Die Indizes für jedes Element in den Kombinationsfeldern verwendet werden angegeben, wenn die Listen, die die Kombinationsfeldern darstellt, in aufgefüllt sind der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Methode in der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Klasse (finden Sie unter [Unterstützung für die Navigationsleiste in einen Legacy-Sprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Diese Indizes Image aus irgendeinem Grund erhalten Sie vom Parser in der Regel durch Ihre Version von den <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Wie die Indizes abgerufen werden, wird alleine Sie.  
  
### <a name="images-used-in-the-error-list-task-window"></a>In der Fehlerliste (Fenster) Aufgabe verwendete Bilder  
 Bei jedem der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser (finden Sie unter [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) ein Fehler auftritt, und übergeben Sie diesen Fehler zu die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode in der <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse, der Fehler wird gemeldet, in der  **Fehlerliste** Aufgabenfenster. Ein Symbol verknüpft werden kann mit jedem Element, das im Fenster Aufgabenliste angezeigt wird und das Symbol stammt vom zurückgegebenen dieselbe Bildliste der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Das Standardverhalten der MPF-Klassen werden nicht auf ein Bild mit der Fehlermeldung angezeigt. Sie können dieses Verhalten jedoch überschreiben, durch das Ableiten einer Klasse von der <xref:Microsoft.VisualStudio.Package.Source> -Klasse und überschreiben die <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> Methode. In dieser Methode erstellen Sie ein neues <xref:Microsoft.VisualStudio.Package.DocumentTask> Objekt. Bevor dieses Objekt zurückgegeben wird, können Sie die <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> Eigenschaft auf die <xref:Microsoft.VisualStudio.Package.DocumentTask> Objekt, das den Bildindex festgelegt. Dies sieht etwa wie im folgenden Beispiel aus. Beachten Sie, dass `TestIconImageIndex` ist eine Enumeration, die alle Symbole aufgeführt und ist spezifisch für dieses Beispiel. Sie müssen möglicherweise eine andere Art der Symbole in der Sprachdienst identifizieren.  
  
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
            TastPriority      priority,  
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
  
## <a name="the-default-image-list-for-a-language-service"></a>Die Standard-Bildliste für einen Sprachdienst  
 Die Standard-Bildliste mit MPF Language-Dienst Basisklassen angegeben enthält eine Reihe von Symbolen, die häufiger Sprachelemente zugeordnet. Der Großteil dieser Symbole sind in Gruppen von sechs Varianten, die für die Access-Konzepte der öffentlich, intern, Friend, geschützt, privat, und Tastenkombinationen angeordnet. Beispielsweise haben Sie eine Methode, je nachdem, ob es öffentlich, geschützt oder privat mit unterschiedlichen Symbolen dargestellt.  
  
 Die folgende Enumeration gibt für jede Symbolsatz typische Namen sowie den zugehörigen Index. Z. B. basierend auf der Enumeration, Sie können angeben den Bildindex für eine geschützte Methode als `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Sie können die Namen in dieser Enumeration nach Bedarf ändern.  
  
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
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Übersicht über die Legacy-Language-Dienst](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
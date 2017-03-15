---
title: "Implementieren eine &#228;ltere Sprache Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Implementieren von Sprachdienste [verwalteten Paketframework]"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Implementieren einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um einen Sprachdienst mithilfe von verwaltetem Paketframeworks \(MPF\) zu implementieren, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse ableiten und die folgenden abstrakten Methoden und Eigenschaften implementiert werden:  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>\-Methode  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>\-Methode  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode  
  
-   Die <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>\-Eigenschaft.  
  
 Folgenden finden Sie die entsprechenden Abschnitte ausführliche Informationen zum Implementieren dieser Methoden und Eigenschaften.  
  
 Um zusätzliche Features zu unterstützen, muss möglicherweise der Sprachdienst eine Klasse von einer der MPF\-Sprachendienst Klassen ableiten. Beispielsweise um zusätzliche Menübefehle zu unterstützen, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter>\-Klasse ableiten und behandlungs Befehl mehrere Methoden überschreiben \(siehe <xref:Microsoft.VisualStudio.Package.ViewFilter> für Details\).  Die <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse stellt mehrere Methoden, die aufgerufen werden, um neue Instanzen unterschiedlicher Klassen zu erstellen, und überschreiben Sie die entsprechende Methode zum Erstellen einer Instanz der Klasse bereitzustellen.  Beispielsweise müssen Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse überschreiben, um eine Instanz der Klasse zurückzugeben, <xref:Microsoft.VisualStudio.Package.ViewFilter> besitzen.  Weitere Informationen finden Sie im Abschnitt „instanziierend der benutzerdefinierten Klassen“.  
  
 Der Sprachdienst kann auch eigene Symbole bieten, die in vielen Stellen verwendet werden.  Wenn z. B. eine IntelliSense\-Vervollständigungsliste angezeigt wird, kann jedes Element in der Liste vorhanden ist, wird ein Symbol zugeordnet ist und das Element als Methode markieren, Namespace, Klasse, Eigenschaft oder was für die Sprache erforderlich ist.  Diese Symbole sind in allen IntelliSense\-Listen **Navigationsleiste**, und klicken Sie im **Fehlerliste** Aufgabenfenster verwendet.  Weitere Informationen finden Sie im Abschnitt „Sprachendienst\-Image“ weiter unten.  
  
## GetLanguagePreferences\-Methode  
 Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>\-Methode gibt immer die gleiche Instanz einer <xref:Microsoft.VisualStudio.Package.LanguagePreferences>\-Klasse zurück.  Sie können die <xref:Microsoft.VisualStudio.Package.LanguagePreferences>\-Klasse verwenden, wenn Sie keine zusätzlichen Einstellungen für den Sprachdienst erfordern.  Die MPF\-Sprachendienst Klassen nehmen das Vorhandensein der mindestens <xref:Microsoft.VisualStudio.Package.LanguagePreferences>\-Klasse.  
  
### Beispiel  
 In diesem Beispiel wird eine typische Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>\-Methode auf.  In diesem Beispiel wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences>\-Klasse.  
  
```c#  
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
  
## GetScanner\-Methode  
 Diese Methode gibt eine Instanz eines <xref:Microsoft.VisualStudio.Package.IScanner>\-Objekts zurück, das einen Zeile\-ausgerichteten Parser oder ein Scanner implementiert, die für das Abrufen von Token und ihre Typen und Trigger verwendet werden.  Dieser Scanner wird in der <xref:Microsoft.VisualStudio.Package.Colorizer>\-Klasse für Farbauftrag verwendet, obwohl der Scanner für das Abrufen von Tokentypen und Triggern als Präfix für einen komplexeren Analysevorgang verwendet werden kann.  Sie müssen die Klasse bereitstellen, die die <xref:Microsoft.VisualStudio.Package.IScanner>\-Schnittstelle implementiert und Sie müssen alle Methoden für die <xref:Microsoft.VisualStudio.Package.IScanner>\-Schnittstelle implementieren.  
  
### Beispiel  
 In diesem Beispiel wird eine typische Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>\-Methode auf.  Die `TestScanner`\-Klasse implementiert die <xref:Microsoft.VisualStudio.Package.IScanner>\-Schnittstelle \(nicht dargestellt\).  
  
```c#  
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
  
## ParseSource\-Methode  
 Analysiert die Quelldatei basierend auf verschiedene Gründe.  Diese Methode ist ein <xref:Microsoft.VisualStudio.Package.ParseRequest>\-Objekt angegeben, das beschreibt, welche von einem bestimmten Analysevorgang erwartet wird.  Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode ruft einen komplexeren Parser, der Token Funktionen und Bereich bestimmt.  Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode wird als Unterstützung für IntelliSense\-Vorgänge sowie die Zuordnung von Klammern verwendet.  Auch wenn Sie keine solchen erweiterten Vorgänge unterstützen, müssen Sie ein gültiges <xref:Microsoft.VisualStudio.Package.AuthoringScope>\-Objekt noch zurückgeben und das müssen Sie eine Klasse erstellen, die die Schnittstelle implementiert und <xref:Microsoft.VisualStudio.Package.AuthoringScope> implementiert alle Methoden in dieser Schnittstelle.  Sie können NULL\-Werte aus allen Methoden zurückgegeben werden, aber das <xref:Microsoft.VisualStudio.Package.AuthoringScope>\-Objekt selbst darf kein NULL\-Wert sein.  
  
### Beispiel  
 In diesem Beispiel wird eine minimale Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>\-Methode und der <xref:Microsoft.VisualStudio.Package.AuthoringScope>\-Klasse aus, um dem Sprachdienst zu ermöglichen, zu kompilieren und zu arbeiten, ohne tatsächlich mehr erweiterten Features zu unterstützen.  
  
```c#  
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
  
## Name\-Eigenschaft  
 Diese Eigenschaft gibt den Namen des Sprachdiensts zurück.  Dies muss derselbe angegebene Name sein, als der Sprachdienst registriert wurde.  Dieser Name wird an mehreren Stellen, das verwendet vorstehendste Argument <xref:Microsoft.VisualStudio.Package.LanguagePreferences> die Klasse darstellt, in der der Name verwendet wird, um die Registrierung zuzugreifen.  Der Name, der von dieser Eigenschaft zurückgegeben wird, dürfen nicht lokalisiert werden, wie er in der Registrierung für Registrierungseintrag und Schlüsselnamen verwendet wird.  
  
### Beispiel  
 In diesem Beispiel wird eine mögliche Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>\-Eigenschaft an.  Beachten Sie, dass der Name hier hartcodiert wird: Der tatsächliche Name sollte aus einer Ressourcendatei abgerufen werden. Daher kann er verwendet werden, wenn ein Sprachdienst registriert werden \(siehe [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
```c#  
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
  
## Benutzerdefinierte Klassen instanziieren  
 Die folgenden Methoden in den angegebenen Klassen überschrieben werden können, um Instanzen bereitzustellen, Versionen jeder Klasse besitzen.  
  
### In der LanguageService\-Klasse  
  
|Methode|Klasse zurückgegeben|Beschreibung|  
|-------------|--------------------------|------------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Um benutzerdefinierte Ergänzungen der Textansicht unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Um benutzerdefinierte Dokumenteigenschaften unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|So **Navigationsleiste**unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|So Supportfunktionen Vorlagen in den Codeausschnitt.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|So zeigen Sie Codeausschnitte unterstützen \(Diese Methode wird i. d. R. nicht außer Kraft gesetzt\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|So Anpassung der <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur \(diese Methode wird in der Regel nicht außer Kraft gesetzt\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|So fügen Sie den Quellcode der Formatierung unterstützen, Kommentarzeichen an Methodensignaturen und passen angibt.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Um zusätzliche Menübefehle unterstützen.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|So Syntax\-Hervorhebung unterstützen \(Diese Methode wird i. d. R. nicht außer Kraft gesetzt\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Um Zugriff auf die Spracheinstellungen unterstützen.  Diese Methode muss implementiert werden, jedoch kann eine Instanz der Basisklasse zurückgeben.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|So fügen Sie einen Parser verwendet zum Identifizieren von Typen von Token in einer Zeile bereitstellen.  Diese Methode muss implementiert werden und <xref:Microsoft.VisualStudio.Package.IScanner> muss abgeleitet werden.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|So fügen Sie einen Parser verwendet zum Identifizieren von Funktionen und Bereich in einer kompletten Quelldatei bereitstellen.  Diese Methode muss implementiert werden und muss eine Instanz der Version der <xref:Microsoft.VisualStudio.Package.AuthoringScope>\-Klasse zurückgeben.  Wenn Sie unterstützen möchten, Syntax\-Hervorhebung \(die den <xref:Microsoft.VisualStudio.Package.IScanner> Parser <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> erfordert, die von der Methode zurückgegeben wird\), können Sie in dieser Methode nichts anderes als eine Version vor der Rückgabe <xref:Microsoft.VisualStudio.Package.AuthoringScope> deren Methoden der Klasse alle null\-werte zurückgeben.|  
  
### In der Quellklasse  
  
|Methode|Klasse zurückgegeben|Beschreibung|  
|-------------|--------------------------|------------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Für das Anpassen der Anzeige von IntelliSense\-Vervollständigungslisten \(diese Methode wird in der Regel nicht außer Kraft gesetzt\).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Für die Unterstützung von Markierungen in der Fehlerliste taskliste. ausdrücklich Unterstützung für Funktionen über dem Öffnen der Datei und das Springen zur Zeile, die den Fehler verursacht hat.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Für das Anpassen der Anzeige der IntelliSense\-Parameterinformationens\-QuickInfo.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Für die Unterstützung des kommentierenden Codes.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Für das Erfassen von Informationen während der Analyse Vorgangs.|  
  
### In der AuthoringScope\-Klasse  
  
|Methode|Klasse zurückgegeben|Beschreibung|  
|-------------|--------------------------|------------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Stellt eine Liste von Deklarationen wie Typen oder Member bereit.  Diese Methode muss implementiert werden, kann aber einen NULL\-Wert zurückgeben.  Wenn diese Methode ein gültiges Objekt zurückgibt, muss das Objekt eine Instanz der Version der <xref:Microsoft.VisualStudio.Package.Declarations>\-Klasse sein.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Stellt eine Liste von Methodensignaturen für einen angegebenen Kontext bereit.  Diese Methode muss implementiert werden, kann aber einen NULL\-Wert zurückgeben.  Wenn diese Methode ein gültiges Objekt zurückgibt, muss das Objekt eine Instanz der Version der <xref:Microsoft.VisualStudio.Package.Methods>\-Klasse sein.|  
  
## Sprachendienst\-Images  
 Um eine Liste der während des Sprachdiensts zu verwendende Symbolen bereitstellen, überschreiben Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse an, und geben Sie <xref:System.Windows.Forms.ImageList> zurück, das die Symbole enthält.  Die Basis\- <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klassenbelastungen ein Standardsatz von Symbolen.  Während Sie den genauen Index des Bildes in diesen Stellen angeben, welche Symbole anordnen, wie Sie benötigen, sind Sie Bildliste Sie vollständig ist.  
  
### IntelliSense\-Vervollständigungslisten in verwendeten Bilds  
 Die IntelliSense\-Vervollständigungslisten wird der Index des Bilds für jedes Element in der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>\-Methode der <xref:Microsoft.VisualStudio.Package.Declarations>\-Klasse angegeben, die Sie überschreiben müssen, wenn Sie einen Index des Bilds bereitstellen möchten.  Der Wert, der aus der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>\-Methode zurückgegeben wird, ist ein Index in der Bildliste, die dem <xref:Microsoft.VisualStudio.Package.CompletionSet>\-Klassenkonstruktor angegeben ist und die ist dieselbe, die aus der Bildliste <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A><xref:Microsoft.VisualStudio.Package.LanguageService>\-Methode in der Klasse zurückgegeben wird \(Sie können ändern, der für <xref:Microsoft.VisualStudio.Package.CompletionSet> die Bildliste zu verwenden, wenn Sie die <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.Source>\-Klasse überschreiben, um eine andere Bildliste anzugeben\).  
  
### Bilder verwendet der Navigationsleiste  
 **Navigationsleiste** wird Auflisten von Typen und Membern an und wird für schnelle Navigation kann Symbole anzeigen verwendet.  Diese Symbole sind in der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse abgerufen und können nicht für **Navigationsleiste**ausdrücklich überschrieben werden.  Die Indizes, die für jedes Element in den Kombinationsfeldern verwendet werden, Listen, wenn angegeben werden, die die Kombinationsfelder darstellen, die <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>\-Klasse aufgefüllt werden \(siehe [Unterstützung für die Navigationsleiste in einem Legacy\-Sprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\).  Diese Bild des Parsers, mit vorhandenen Indizes werden in der Regel durch die Version der <xref:Microsoft.VisualStudio.Package.Declarations>\-Klasse ermittelt.  Wie die Indizes abgerufen werden. Sie ist vollständig  
  
### Bilder werden im Fehlerlisten\-Aufgaben\-Fenster  
 Sobald der Parser Methoden <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(siehe [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)\), ein Fehler auftritt und diesen Fehler zu <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.AuthoringSink>\-Klasse erreicht, wird der Fehler im **Fehlerliste** Aufgabenfenster gemeldet.  Ein Symbol kann mit jedem Element zugeordnet sind, das im Aufgabenfenster wird und das Symbol aus der Bildliste stammt, die aus der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>\-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>\-Klasse zurückgegeben wird.  Das Standardverhalten der MPF\-Klassen ist, ein Bild mit der Fehlermeldung nicht angezeigt.  Sie können dieses Verhalten überschreiben, indem Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source>\-Klasse ableiten und die <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>\-Methode überschreiben.  In dieser Methode erstellen Sie ein neues <xref:Microsoft.VisualStudio.Package.DocumentTask>\-Objekt.  Bevor Sie dieses Objekt zurückgeben, können Sie die <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>\-Eigenschaft auf dem <xref:Microsoft.VisualStudio.Package.DocumentTask>\-Objekt verwenden, um den Index des Bilds festlegen.  Dies würde in etwa dem folgenden Beispiel entsprechen.  Beachten Sie, dass `TestIconImageIndex` eine Enumeration ist, die alle Symbole aufgeführt ist und diesem Beispiel spezifisch sind.  Sie haben möglicherweise eine andere Art von Identifizieren von Symbolen im Sprachdienst.  
  
```c#  
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
  
## Der Standardwert für die Bildliste für einen Sprachdienst  
 Der Standardwert für die Bildliste, die mit den Klassen der Sprachdienst Basis MPF angegeben wird, umfasst mehrere Symbole, die mit den mehr Elementen die gemeinsame Sprache zugeordnet sind.  Die Großteil dieser Symbole werden in den Sätzen von sechs Variationen, entsprechend den Zugriff konzepten der öffentlichen angeordnet, intern, Friend, privat, geschützt und Verknüpfung.  Beispielsweise können Sie verschiedene Symbole für eine Methode aufweisen, je nachdem, ob sie öffentlich oder privat, geschützt ist, oder legt diesen fest.  
  
 Die folgende Enumeration gibt typische Namen für jedes festgelegte Symbol an und gibt den zugeordneten Index an.  Zum Beispiel auf Grundlage der Enumeration, können Sie den Index des Bilds für geschützte Methode als `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`angeben.  Sie können die Namen in dieser Enumeration ändern, wie gewünscht.  
  
```c#  
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
  
## Siehe auch  
 [Implementieren einer Legacy\-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Ältere Sprache Service\-Übersicht](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
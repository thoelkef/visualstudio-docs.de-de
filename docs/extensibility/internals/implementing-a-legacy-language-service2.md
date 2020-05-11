---
title: Implementieren eines Legacy-Sprachdienstes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707680"
---
# <a name="implementing-a-legacy-language-service"></a>Implementieren eines Legacysprachdiensts
Um einen Sprachdienst mit dem Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Package.LanguageService> zu implementieren, müssen Sie eine Klasse aus der Klasse ableiten und die folgenden abstrakten Methoden und Eigenschaften implementieren:

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> -Methode

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> -Methode

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>-Eigenschaft.

  Weitere Informationen zur Implementierung dieser Methoden und Eigenschaften finden Sie in den entsprechenden Abschnitten weiter unten.

  Um zusätzliche Funktionen zu unterstützen, muss Ihr Sprachdienst möglicherweise eine Klasse von einer der MPF-Sprachdienstklassen ableiten. Um beispielsweise zusätzliche Menübefehle zu unterstützen, müssen Sie <xref:Microsoft.VisualStudio.Package.ViewFilter> eine Klasse von der Klasse ableiten und mehrere Befehlsbehandlungsmethoden außer Kraft setzen (Details siehe). <xref:Microsoft.VisualStudio.Package.ViewFilter> Die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse stellt eine Reihe von Methoden bereit, die aufgerufen werden, um neue Instanzen verschiedener Klassen zu erstellen, und Sie überschreiben die entsprechende Erstellungsmethode, um eine Instanz Ihrer Klasse bereitzustellen. Sie müssen z. B. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> die <xref:Microsoft.VisualStudio.Package.LanguageService> Methode in der Klasse <xref:Microsoft.VisualStudio.Package.ViewFilter> überschreiben, um eine Instanz Ihrer eigenen Klasse zurückzugeben. Weitere Informationen finden Sie im Abschnitt "Instantiierende benutzerdefinierte Klassen".

  Ihr Sprachdienst kann auch eigene Symbole bereitstellen, die an vielen Orten verwendet werden. Wenn z. B. eine IntelliSense-Vervollständigungsliste angezeigt wird, kann jedem Element in der Liste ein Symbol zugeordnet sein, das das Element als Methode, Klasse, Namespace, Eigenschaft oder was für Ihre Sprache erforderlich ist. Diese Symbole werden in allen IntelliSense-Listen, in der **Navigationsleiste**und im Aufgabenfenster **Fehlerliste** verwendet. Weitere Informationen finden Sie im Abschnitt "Sprachdienstbilder" weiter unten.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences-Methode
 Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode gibt immer dieselbe <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Instanz einer Klasse zurück. Sie können die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Basisklasse verwenden, wenn Sie keine zusätzlichen Einstellungen für Ihren Sprachdienst benötigen. Die MPF-Sprachdienstklassen nehmen das Vorhandensein <xref:Microsoft.VisualStudio.Package.LanguagePreferences> von mindestens der Basisklasse an.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> typische Implementierung der Methode. In diesem Beispiel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> wird die Basisklasse verwendet.

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
 Diese Methode gibt eine <xref:Microsoft.VisualStudio.Package.IScanner> Instanz eines Objekts zurück, das einen zeilenorientierten Parser oder Scanner implementiert, der zum Abrufen von Token und deren Typen und Trigger verwendet wird. Dieser Scanner wird <xref:Microsoft.VisualStudio.Package.Colorizer> in der Klasse für die Farbgebung verwendet, obwohl der Scanner auch zum Abrufen von Tokentypen und Triggern als Vorspiel zu einem komplexeren Analysevorgang verwendet werden kann. Sie müssen die Klasse angeben, die die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle implementiert, <xref:Microsoft.VisualStudio.Package.IScanner> und Sie müssen alle Methoden auf der Schnittstelle implementieren.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> typische Implementierung der Methode. Die `TestScanner` Klasse implementiert <xref:Microsoft.VisualStudio.Package.IScanner> die Schnittstelle (nicht angezeigt).

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
 Analysiert die Quelldatei aus verschiedenen Gründen. Dieser Methode wird <xref:Microsoft.VisualStudio.Package.ParseRequest> ein Objekt gegeben, das beschreibt, was von einem bestimmten Analysevorgang erwartet wird. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode ruft einen komplexeren Parser auf, der die Tokenfunktionalität und den Bereich bestimmt. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode wird zur Unterstützung von IntelliSense-Vorgängen sowie zur Abgleich von Geschweifklammern verwendet. Auch wenn Sie solche erweiterten Vorgänge nicht unterstützen, <xref:Microsoft.VisualStudio.Package.AuthoringScope> müssen Sie dennoch ein gültiges Objekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> zurückgeben, und dazu müssen Sie eine Klasse erstellen, die die Schnittstelle implementiert, und alle Methoden auf dieser Schnittstelle implementieren. Sie können NULL-Werte von <xref:Microsoft.VisualStudio.Package.AuthoringScope> allen Methoden zurückgeben, aber das Objekt selbst darf kein NULL-Wert sein.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> minimale Implementierung <xref:Microsoft.VisualStudio.Package.AuthoringScope> der Methode und der Klasse, die ausreicht, um dem Sprachdienst das Kompilieren und Funktionieren zu ermöglichen, ohne tatsächlich eine der erweiterten Funktionen zu unterstützen.

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
 Diese Eigenschaft gibt den Namen des Sprachdienstes zurück. Dies muss derselbe Name sein, der bei der Registrierung des Sprachdienstes angegeben wurde. Dieser Name wird an einer Reihe von Stellen verwendet, von denen der bekannteste die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse ist, in der der Name für den Zugriff auf die Registrierung verwendet wird. Der von dieser Eigenschaft zurückgegebene Name darf nicht lokalisiert werden, da er in der Registrierung für Registrierungseinträge und Schlüsselnamen verwendet wird.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> mögliche Implementierung der Eigenschaft. Beachten Sie, dass der Name hier hartcodiert ist: Der tatsächliche Name sollte aus einer Ressourcendatei abgerufen werden, damit er bei der Registrierung eines Sprachdienstes verwendet werden kann (siehe [Registrieren eines Legacy-Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Instanziieren von benutzerdefinierten Klassen
 Die folgenden Methoden in den angegebenen Klassen können überschrieben werden, um Instanzen Ihrer eigenen Versionen jeder Klasse bereitzustellen.

### <a name="in-the-languageservice-class"></a>In der LanguageService-Klasse

|Methode|Klasse zurückgegeben|BESCHREIBUNG|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|So unterstützen Sie benutzerdefinierte Ergänzungen zur Textansicht.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|So unterstützen Sie benutzerdefinierte Dokumenteigenschaften.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|So unterstützen Sie die **Navigationsleiste**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Unterstützung von Funktionen in Codeausschnittvorlagen.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Zur Unterstützung von Codeausschnitten (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Um die Anpassung <xref:Microsoft.VisualStudio.Package.ParseRequest> der Struktur zu unterstützen (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Um das Formatieren von Quellcode zu unterstützen, geben Sie Kommentarzeichen an, und passen Sie Methodensignaturen an.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Um zusätzliche Menübefehle zu unterstützen.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Zur Unterstützung der Syntaxhervorhebung (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Unterstützung des Zugriffs auf Spracheinstellungen. Diese Methode muss implementiert sein, kann jedoch eine Instanz der Basisklasse zurückgeben.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|So stellen Sie einen Parser bereit, der zum Identifizieren von Tokentypen in einer Zeile verwendet wird. Diese Methode muss <xref:Microsoft.VisualStudio.Package.IScanner> implementiert und abgeleitet werden.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Bereitstellen eines Parsers, der zum Identifizieren von Funktionen und Bereichen in einer gesamten Quelldatei verwendet wird. Diese Methode muss implementiert sein und eine Instanz <xref:Microsoft.VisualStudio.Package.AuthoringScope> Ihrer Version der Klasse zurückgeben. Wenn Sie nur Syntaxhervorhebung unterstützen möchten <xref:Microsoft.VisualStudio.Package.IScanner> (die den <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> von der Methode zurückgegebenen Parser erfordert), <xref:Microsoft.VisualStudio.Package.AuthoringScope> können Sie in dieser Methode nichts anderes tun, als eine Version der Klasse zurückzugeben, deren Methoden alle NULL-Werte zurückgeben.|

### <a name="in-the-source-class"></a>In der Quellklasse

|Methode|Klasse zurückgegeben|BESCHREIBUNG|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Zum Anpassen der Anzeige von IntelliSense-Vervollständigungslisten (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Zur Unterstützung von Markern in der Aufgabenliste fehlersuche; Unterstützung für Features, die über das Öffnen der Datei hinausgehen und zur Zeile springen, die den Fehler verursacht hat.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Zum Anpassen der Anzeige von IntelliSense Parameter Info ToolTips.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Zum Unterstützen von Kommentarcode.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Zum Sammeln von Informationen während des Analysevorgangs.|

### <a name="in-the-authoringscope-class"></a>In der AuthoringScope-Klasse

|Methode|Klasse zurückgegeben|BESCHREIBUNG|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Stellt eine Liste von Deklarationen wie Membern oder Typen bereit. Diese Methode muss implementiert werden, kann jedoch einen NULL-Wert zurückgeben. Wenn diese Methode ein gültiges Objekt zurückgibt, muss <xref:Microsoft.VisualStudio.Package.Declarations> das Objekt eine Instanz Ihrer Version der Klasse sein.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Stellt eine Liste von Methodensignaturen für einen bestimmten Kontext bereit. Diese Methode muss implementiert werden, kann jedoch einen NULL-Wert zurückgeben. Wenn diese Methode ein gültiges Objekt zurückgibt, muss <xref:Microsoft.VisualStudio.Package.Methods> das Objekt eine Instanz Ihrer Version der Klasse sein.|

## <a name="language-service-images"></a>Sprachdienst Bilder
 Um eine Liste der Symbole bereitzustellen, die im <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> gesamten Sprachdienst verwendet werden sollen, überschreiben Sie die Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse, und geben Sie eine <xref:System.Windows.Forms.ImageList> mit den Symbolen zurück. Die <xref:Microsoft.VisualStudio.Package.LanguageService> Basisklasse lädt einen Standardsatz von Symbolen. Da Sie den genauen Bildindex an den Stellen angeben, die Symbole benötigen, liegt die Anordnung Ihrer eigenen Bildliste ganz bei Ihnen.

### <a name="images-used-in-intellisense-completion-lists"></a>In IntelliSense-Vervollständigungslisten verwendete Bilder
 Für IntelliSense-Vervollständigungslisten wird der Bildindex <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> für <xref:Microsoft.VisualStudio.Package.Declarations> jedes Element in der Methode der Klasse angegeben, die Sie überschreiben müssen, wenn Sie einen Bildindex angeben möchten. Der von der <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Methode zurückgegebene Wert ist ein <xref:Microsoft.VisualStudio.Package.CompletionSet> Index in der Bildliste, der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> dem Klassenkonstruktor zurückgegeben wird, und das ist dieselbe Bildliste, die von der Methode in <xref:Microsoft.VisualStudio.Package.LanguageService> der Klasse zurückgegeben wird (Sie können ändern, welche Bildliste für <xref:Microsoft.VisualStudio.Package.CompletionSet> die verwendet werden soll, wenn Sie die <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse überschreiben, um eine andere Bildliste zu liefern).

### <a name="images-used-in-the-navigation-bar"></a>In der Navigationsleiste verwendete Bilder
 Die **Navigationsleiste** zeigt Listen von Typen und Membern an und wird für die schnelle Navigation verwendet, um Symbole anzuzeigen. Diese Symbole werden <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> von der <xref:Microsoft.VisualStudio.Package.LanguageService> Methode in der Klasse abgerufen und können nicht speziell für die **Navigationsleiste**überschrieben werden. Die Indizes, die für jedes Element in den Kombinationsfeldern verwendet werden, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> werden <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> angegeben, wenn die Listen, die die Kombinationsfelder darstellen, in der Methode in der Klasse ausgefüllt werden (siehe [Unterstützung für die Navigationsleiste in einem Legacy-Sprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Diese Bildindizes werden irgendwie vom Parser abgerufen, <xref:Microsoft.VisualStudio.Package.Declarations> in der Regel über Ihre Version der Klasse. Wie die Indizes erhalten werden, liegt ganz bei Ihnen.

### <a name="images-used-in-the-error-list-task-window"></a>Im Taskfenster Fehlerliste verwendete Bilder
 Immer <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wenn der Methodenparser (siehe [Legacy Language Service Parser and](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Scanner ) <xref:Microsoft.VisualStudio.Package.AuthoringSink> auf einen Fehler stößt und diesen Fehler an die Methode in der Klasse übergibt, wird der Fehler im Taskfenster **Fehlerliste** gemeldet. Jedem Element, das im Aufgabenfenster angezeigt wird, kann ein Symbol zugeordnet werden, und dieses Symbol stammt aus derselben Bildliste, die von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse zurückgegeben wird. Das Standardverhalten der MPF-Klassen besteht darin, kein Bild mit der Fehlermeldung anzuzeigen. Sie können dieses Verhalten jedoch überschreiben, indem <xref:Microsoft.VisualStudio.Package.Source> Sie eine Klasse <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> von der Klasse ableiten und die Methode überschreiben. In dieser Methode erstellen <xref:Microsoft.VisualStudio.Package.DocumentTask> Sie ein neues Objekt. Bevor Sie dieses Objekt zurückgeben, können Sie die <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> Eigenschaft für das <xref:Microsoft.VisualStudio.Package.DocumentTask> Objekt verwenden, um den Bildindex festzulegen. Dies würde etwa wie das folgende Beispiel aussehen. Beachten `TestIconImageIndex` Sie, dass es sich um eine Enumeration handelt, die alle Symbole auflistet und für dieses Beispiel spezifisch ist. Möglicherweise haben Sie eine andere Möglichkeit, Symbole in Ihrem Sprachdienst zu identifizieren.

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

## <a name="the-default-image-list-for-a-language-service"></a>Die Standardbildliste für einen Sprachdienst
 Die Standardbildliste, die den Basis-MPF-Sprachdienstklassen zur Verfügung gestellt wird, enthält eine Reihe von Symbolen, die den gebräuchlicheren Sprachelementen zugeordnet sind. Der Großteil dieser Symbole ist in Sätzen von sechs Variationen angeordnet, die den Zugangskonzepten von public, internal, friend, protected, private und shortcut entsprechen. Sie können z. B. unterschiedliche Symbole für eine Methode haben, je nachdem, ob sie öffentlich, geschützt oder privat ist.

 Die folgende Enumeration gibt typische Namen für jeden Symbolsatz und den zugeordneten Index an. Auf der Grundlage der Enumeration können Sie z. B. `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`den Bildindex für eine geschützte Methode als angeben. Sie können die Namen in dieser Enumeration wie gewünscht ändern.

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

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

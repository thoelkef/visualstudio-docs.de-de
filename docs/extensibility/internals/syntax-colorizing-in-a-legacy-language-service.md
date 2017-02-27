---
title: "Farbliche Kennzeichnung von Syntax in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste [Verwaltetes Paketframework], syntaxhervorhebung"
  - "farbliche Kennzeichnung, Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "Syntax hervorheben, Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "Sprachdienste [Verwaltetes Paketframework], die farbliche Kennzeichnung"
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Farbliche Kennzeichnung von Syntax in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Syntax farblich markiert ist eine Funktion, durch die verschiedenen Elemente einer Programmiersprache, die in einer Quelldatei in verschiedenen Farben und Stile angezeigt werden. Um dieses Feature zu unterstützen, müssen Sie angeben, einen Parser oder Scanner, die die lexikalische Elemente oder Token in der Datei identifizieren kann. Viele Sprachen unterscheiden, Schlüsselwörter, Trennzeichen \(z. B. runden oder geschweiften Klammern\) und Kommentare werden auf unterschiedliche Weise färben.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Erweitern der\-Editor und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Implementierung  
 Unterstützung für die farbliche Kennzeichnung der verwalteten Paketframework \(MPF\) enthält die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle. Diese Klasse interagiert mit einer <xref:Microsoft.VisualStudio.Package.IScanner> zur Ermittlung des Tokens und Farben. Weitere Informationen zu Scanner, finden Sie unter [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse kennzeichnet jedes Zeichens des Tokens mit den Informationen für die Farbe, und gibt diese Informationen zum Anzeigen der Quelldatei\-Editor.  
  
 Die Farbinformationen zurückgegeben, die in den Editor ist ein Index in eine Liste von färbbare Elemente. Jede färbbare Element gibt einen Farbwert und einen Satz von Schriftartattributen, z. B. fett oder durchgestrichen. Der Editor stellt einen Satz von standardmäßigen färbbare\-Elemente, die der Sprachdienst verwenden kann. Müssen Sie lediglich die entsprechende Farbe für jeden Tokentyp angeben. Sie können jedoch stellen benutzerdefinierte färbbare Elemente und die Indizes, die Sie angeben, für die Token und eine eigene Liste von färbbare Elemente anstelle der standardmäßigen Liste verweisen. Müssen Sie auch Festlegen der `RequestStockColors` Registrierungseintrag auf 0 \(oder geben Sie die `RequestStockColors` Eintrag überhaupt\) zur Unterstützung von benutzerdefinierter Farben. Lassen sich dieses Registrierungseintrags mit benannten Parameter für die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> benutzerdefiniertes Attribut. Weitere Informationen zum registriert eine Sprachdienst und zum Festlegen von Optionen finden Sie unter [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## Benutzerdefinierte Färbbare Elemente  
 Um eine eigene benutzerdefinierte färbbare Elemente angeben möchten, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> und <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Die erste Methode gibt die Anzahl der benutzerdefinierten färbbare Elemente, die der Sprachdienst unterstützt, und das zweite das benutzerdefinierte färbbare Element anhand des Indexes ab. Sie erstellen die Standardliste der benutzerdefinierte färbbare Elemente. Im Konstruktor des Dienstes Sprache alles, was Sie tun müssen ist Geben Sie jede färbbare Element mit einem Namen. Visual Studio verarbeitet automatisch den Fall, in dem der Benutzer einen anderen Satz von färbbare Elemente auswählt. Dieser Name wird in der **Schriftarten und Farben** Eigenschaftenseite auf die **Optionen** \(Dialogfeld\) \(in Visual Studio verfügbar **Tools** im Menü\) und dieser Name bestimmt, welche Farbe ein Benutzer überschrieben hat. Auswahl des Benutzers in einem Cache in der Registrierung gespeichert und durch den Namen zugegriffen. Die **Schriftarten und Farben** Eigenschaftenseite enthält eine Liste aller Farbnamen in alphabetischer Reihenfolge, damit Sie benutzerdefinierten Farben gruppieren können, indem Sie vor jedem Namen Farbe durch den Namen Ihres Language; z. B. "**TestLanguage \- Kommentar**"und"**TestLanguage \- Schlüsselwort**". Oder Sie können Ihre färbbare Elemente gruppieren nach Typ "**Kommentar \(TestLanguage\)**"und"**Schlüsselwort \(TestLanguage\)**". Gruppieren nach Sprache wird bevorzugt.  
  
> [!CAUTION]
>  Es wird dringend empfohlen, enthalten den Namen der färbbare Elementname, Konflikte mit vorhandenen Namen von färbbare Element zu vermeiden.  
  
> [!NOTE]
>  Wenn Sie während der Entwicklung der Name eines Farben ändern, müssen Sie den Cache zurücksetzen, den Visual Studio beim ersten Farben zugegriffen wurde erstellt. Dazu können Sie mit der **Zurücksetzen der experimentellen Struktur** Befehl aus der Visual Studio SDK.  
  
 Beachten Sie, dass das erste Element in der Liste der färbbare Elemente nie verwiesen wird. Visual Studio stellt immer die Standardfarben für Text und die Attribute für dieses Element. Die einfachste Möglichkeit für den Umgang mit diesem ist ein Platzhalter färbbare Element als erstes Element angeben.  
  
### High Color Färbbare Elemente  
 Färbbare Elemente können auch über 24\-Bit\- oder hohe Farbwerte unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle. Die MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> \-Klasse unterstützt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> \-Schnittstelle und die 24\-Bit\-Farben werden im Konstruktor zusammen mit der normalen Farben angegeben. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.ColorableItem> \-Klasse für weitere Details. Das folgende Beispiel zeigt, wie die 24\-Bit\-Farben für Schlüsselwörter und Kommentare festgelegt wird. Die 24\-Bit\-Farben werden verwendet, wenn auf dem Desktop des Benutzers 24\-Bit\-Farbe unterstützt wird. Andernfalls werden die normalen Textfarben verwendet.  
  
 Beachten Sie, dass dies die Standardfarben für Ihre Sprache sind; der Benutzer kann diese Farben nach Belieben ändern.  
  
### Beispiel  
 Dieses Beispiel zeigt eine Möglichkeit zum Deklarieren und füllen ein Array von benutzerdefinierten färbbare Elemente mithilfe der <xref:Microsoft.VisualStudio.Package.ColorableItem> Klasse. Diesem Beispiel wird die Schlüsselwort und Kommentar Farben mit 24\-Bit\-Farben.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## Die Klasse zur Farbdarstellung und der Scanner  
 Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> \-Klasse verfügt über eine <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> Methode, Instantiantes der <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse. Der Scanner, die von zurückgegeben wird die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> \-Methode übergeben, um die <xref:Microsoft.VisualStudio.Package.Colorizer> \-Klassenkonstruktor.  
  
 Sie implementieren, müssen die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> \-Methode in eine eigene Version von der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Die <xref:Microsoft.VisualStudio.Package.Colorizer> \-Klasse verwendet den Scanner, um alle token Farbinformationen abzurufen.  
  
 Der Scanner muss zum Auffüllen einer <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur es findet für jedes Token. Diese Struktur enthält Informationen, wie z. B. die Spanne der Token, belegt den Farbe Index zu verwenden, welcher Typ von Tokens, und Trigger wird \(finden Sie unter <xref:Microsoft.VisualStudio.Package.TokenTriggers>\). Nur der Index Zeitspanne und Farbe für die farbliche Kennzeichnung von erforderlich sind die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse.  
  
 Der Color\-Index gespeichert wird, der <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur ist in der Regel einen Wert aus der <xref:Microsoft.VisualStudio.Package.TokenColor> Enumeration bietet eine Reihe von benannten Indizes, die für verschiedene Sprachelemente wie Schlüsselwörter und Operatoren. Wenn Ihre benutzerdefinierte färbbare Elemente entspricht die Liste der Elemente angezeigt, der <xref:Microsoft.VisualStudio.Package.TokenColor> \-Enumeration, und Sie können einfach verwenden die Enumeration als Farbe für jedes Token. Allerdings können Wenn zusätzliche färbbare Elemente enthalten sind, oder Sie nicht die vorhandenen Werte in dieser Reihenfolge verwenden möchten, Sie Anordnen der Liste benutzerdefinierte färbbare Elemente entsprechend dem Bedarf Ihrer und den entsprechenden Index in der Liste zurückzugeben. Denken Sie wandeln Sie den Index auf eine <xref:Microsoft.VisualStudio.Package.TokenColor> in zum Speichern der <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] sieht nur den Index.  
  
### Beispiel  
 Das folgende Beispiel zeigt, wie der Scanner drei Tokentypen identifizieren kann: Zahlen, Satzzeichen und Bezeichner \(alles, was keine Zahl oder ein Satzzeichen ist\). In diesem Beispiel wird nur zu Illustrationszwecken und stellt eine umfassende Implementierung Parser und Scanner nicht dar. Es wird vorausgesetzt, dass ein `Lexer` \-Klasse mit einer `GetNextToken()` Methode, die eine Zeichenfolge zurückgibt.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)
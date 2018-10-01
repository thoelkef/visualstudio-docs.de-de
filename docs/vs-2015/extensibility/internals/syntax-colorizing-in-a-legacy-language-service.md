---
title: Einfärben der Syntax in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57d8115be296beba910da7a1bdb1019645c0ee5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510144"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Einfärben der Syntax in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [einfärben der Syntax in einem Legacysprachdienst](https://docs.microsoft.com/visualstudio/extensibility/internals/syntax-colorizing-in-a-legacy-language-service).  
  
Farbliche Markierung der Syntax ist ein Feature, das bewirkt, dass verschiedene Elemente in einer Programmiersprache, die in einer Quelldatei in unterschiedlichen Farben und Stile angezeigt werden. Um dieses Feature zu unterstützen, müssen Sie angeben, einen Parser oder den Scanner, die Typen von lexikalischen Elemente oder Token in der Datei identifizieren kann. Viele Sprachen unterscheiden, Schlüsselwörter, Trennzeichen (z. B. das runden oder geschweiften Klammern) und Kommentare farbliche Kennzeichnung von ihnen auf unterschiedliche Weise.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweitern des Editors und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementation"></a>Implementierung  
 Die farbliche Kennzeichnung zur Unterstützung des managed Package Framework (MPF) enthält die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle. Diese Klasse interagiert mit einer <xref:Microsoft.VisualStudio.Package.IScanner> zur Ermittlung des Tokens und Farben. Weitere Informationen zu den Scanner, finden Sie unter [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse kennzeichnet jedes Zeichen des Tokens mit den Informationen für die Farbe, und gibt diese Informationen zum Anzeigen der Quelldatei-Editor.  
  
 Die Farbinformationen für den Editor zurückgegeben wird ein Index in eine Liste der kolorierbaren Elemente. Jede kolorierbare Element gibt einen Farbwert und einen Satz von Schriftartattributen, z. B. fett oder durchgestrichen. Der Editor stellt einen Satz von standardmäßigen kolorierbaren Elemente, die der Sprachdienst verwenden können. Alles, was Sie tun müssen ist, geben Sie den Index der entsprechenden Farbe für jeden Tokentyp. Sie können jedoch bieten eine Reihe von benutzerdefinierten kolorierbaren Elemente und die Indizes, die Sie angeben, für die Token und eine eigene Liste der kolorierbaren Elemente, die anstelle der Standardliste verweisen. Müssen Sie auch Festlegen der `RequestStockColors` Registrierungseintrag auf 0 (oder geben Sie nicht die `RequestStockColors` Eintrag überhaupt) zur Unterstützung benutzerdefinierter Farben. Sie können diesen Registrierungseintrag mit dem ein benannter Parameter, Festlegen der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> benutzerdefiniertes Attribut. Weitere Informationen zu einen Sprachdienst zu registrieren und Festlegen der Optionen, finden Sie unter [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Benutzerdefinierte einfärbbare Elemente  
 Um Ihre eigenen benutzerdefinierten kolorierbaren Elemente angeben möchten, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> und <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Die erste Methode gibt die Anzahl der benutzerdefinierten kolorierbaren Elemente, die der Sprachdienst unterstützt, und die zweite das benutzerdefinierte färbbare Element anhand des Indexes ab. Sie erstellen die Standardliste der benutzerdefinierten kolorierbaren Elemente. Im Konstruktor des Sprachdiensts alles, was Sie tun müssen ist Geben Sie jede kolorierbaren Elements mit einem Namen. Visual Studio behandelt automatisch den Fall, in denen der Benutzer einen anderen Satz von einfärbbaren Elementen auswählt. Dieser Name wird in angezeigt der **Schriftarten und Farben** Eigenschaftenseite auf die **Optionen** im Dialogfeld (verfügbar in Visual Studio **Tools** Menü) und bestimmt, welche dieser Name die Farbe, die ein Benutzer außer Kraft gesetzt hat. Auswahl des Benutzers werden in einem Cache in der Registrierung gespeichert und der Farbname zugreifen. Die **Schriftarten und Farben** auf der Seite zeigt eine Liste aller Farbnamen in alphabetischer Reihenfolge, damit Sie Ihre benutzerdefinierten Farben gruppieren können, jeder Farbname durch den Namen Ihres Language; abgrenzen, indem Sie z. B. "**TestLanguage kommentierten**"und"**TestLanguage - Schlüsselwort**". Oder Sie können Ihre kolorierbaren Elemente nach Typ gruppieren "**Kommentar (TestLanguage)**"und"**Schlüsselwort (TestLanguage)**". Eine Gruppierung nach Sprachnamen wird bevorzugt.  
  
> [!CAUTION]
>  Es wird dringend empfohlen, dass Sie die Namen der Sprache in den kolorierbaren Elements-Namen, um Konflikte mit vorhandenen kolorierbaren Elementnamen zu vermeiden einschließen.  
  
> [!NOTE]
>  Wenn Sie während der Entwicklung den Namen eines Ihrer Farben ändern, müssen Sie den Cache zurücksetzen, den Visual Studio erstmals erstellt, die Sie Farben auf die zugegriffen wurde. Dazu können Sie mit der **Zurücksetzen der experimentellen Struktur** Befehl der Visual Studio SDK-Programme.  
  
 Beachten Sie, dass das erste Element in der Liste der kolorierbaren Elemente nie darauf verwiesen wird. Visual Studio stellt immer die Standardfarben für Text und die Attribute für dieses Element. Die einfachste Möglichkeit für den Umgang mit diesem ist ein Platzhalter färbbares Element als erstes Element angeben.  
  
### <a name="high-color-colorable-items"></a>Hoher Farbtiefe Einfärbbaren Elementen  
 Einfärbbare Elementen unterstützt auch 24-Bit-oder eine hohe Werte über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle. Das MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> -Klasse unterstützt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> -Schnittstelle und die 24-Bit-Farben werden in den Konstruktor zusammen mit der normalen Farben angegeben. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.ColorableItem>-Klasse. Das folgende Beispiel zeigt, wie Sie die 24-Bit-Farben für Schlüsselwörter und Kommentare festgelegt wird. Die 24-Bit-Farben werden verwendet, wenn 24-Bit-Farben, die auf dem Desktop des Benutzers unterstützt wird. Andernfalls werden die normalen Textfarben verwendet.  
  
 Beachten Sie, dass dies die Standardfarben für Ihre Sprache sind; der Benutzer kann diese Farben nach Belieben ändern.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Möglichkeit zum Deklarieren und füllen ein Array der benutzerdefinierten kolorierbaren Elemente, die mit der <xref:Microsoft.VisualStudio.Package.ColorableItem> Klasse. In diesem Beispiel wird die Stichwort- und Kommentartext Farben, die mit 24-Bit-Farben an.  
  
```csharp  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>Die Farbauswahl-Klasse und der Überprüfung  
 Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse verfügt über eine <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> Methode diese Instantiantes der <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse. Die Überprüfung, die von zurückgegeben wird die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode übergeben wird, um die <xref:Microsoft.VisualStudio.Package.Colorizer> Klassenkonstruktor.  
  
 Sie implementieren, müssen die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> -Methode in Ihre eigene Version der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse verwendet die Überprüfung, um alle token Farbinformationen abzurufen.  
  
 Füllen Sie die Überprüfung muss eine <xref:Microsoft.VisualStudio.Package.TokenInfo> -Struktur es findet für jedes Token. Diese Struktur enthält Informationen, wie z. B. die Spanne des Tokens, nimmt den Farbenindex, verwenden Sie, welche Art der token, und Triggern handelt es sich (finden Sie unter <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Nur der Spanne und Farbe Index sind erforderlich, für die farbliche Kennzeichnung von der <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse.  
  
 Der Color-Index gespeichert wird, der <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur ist in der Regel einen Wert aus der <xref:Microsoft.VisualStudio.Package.TokenColor> -Enumeration, die eine Anzahl von benannten Indizes, die für verschiedene Sprachelemente wie Schlüsselwörter und Operatoren enthält. Wenn Ihre benutzerdefinierten kolorierbaren Elemente Übereinstimmungen Auflisten der Elemente angezeigt, der <xref:Microsoft.VisualStudio.Package.TokenColor> -Enumeration, Sie können nur verwenden Sie die Enumeration als Farbe für jedes Token. Allerdings können, wenn Sie zusätzliche kolorierbaren Elemente haben, oder Sie nicht die vorhandenen Werte in dieser Reihenfolge verwenden möchten, Sie Anordnen der Liste der benutzerdefinierten kolorierbaren Elemente gemäß Ihren Anforderungen und den entsprechenden Index in der Liste zurückgegeben. Achten Sie nur den Index Umwandeln einer <xref:Microsoft.VisualStudio.Package.TokenColor> beim Speichern in der <xref:Microsoft.VisualStudio.Package.TokenInfo> -Struktur [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] sieht nur den Index.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die Überprüfung auf drei Typen von Sicherheitstoken identifizieren kann: Zahlen, Interpunktionszeichen und Bezeichnern (alles, was keine Zahl oder ein Interpunktionszeichen ist). In diesem Beispiel wird nur zu Illustrationszwecken und keine umfassendere Parser und Scanner-Implementierung darstellt. Es wird vorausgesetzt, dass eine `Lexer` -Klasse mit einem `GetNextToken()` -Methode, die eine Zeichenfolge zurückgibt.  
  
```csharp  
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
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Ältere Sprachdienstparser und -Überprüfung](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)


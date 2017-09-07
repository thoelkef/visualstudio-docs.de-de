---
title: Farbliche Kennzeichnung von Syntax in ein Legacy-Sprachdienst | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1ec6732b511d437a24149d9cd4b20e593a13a8f0
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Farbliche Kennzeichnung von Syntax in ein Legacy-Sprachdienst
Syntaxhervorhebung ist ein Feature, das bewirkt, dass andere Elemente von einer Programmiersprache Ihrer Wahl, die in einer Quelldatei in verschiedenen Farben und Formaten angezeigt werden. Um dieses Feature zu unterstützen, müssen Sie angeben, ein Parser oder Scanner, die die lexikalische Elemente oder Token in der Datei identifizieren kann. Viele Sprachen unterscheiden, Schlüsselwörter, Trennzeichen (z. B. runden oder geschweiften Klammern) und Kommentaren farbliche Kennzeichnung von ihnen auf unterschiedliche Weise.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweiterung des Editors und des Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementation"></a>Implementierung  
 Farbliche Kennzeichnung zur Unterstützung des managed Package Framework (MPF) enthält die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle. Diese Klasse interagiert mit einer <xref:Microsoft.VisualStudio.Package.IScanner> zur Ermittlung des Tokens und Farben. Weitere Informationen zum Scanner, finden Sie unter [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse kennzeichnet jedes Zeichens des Tokens mit den Informationen für die Farbe, und gibt diese Informationen in den Editor Anzeigen der Quelldatei.  
  
 Die Farbe Informationen zurückgegeben, die auf den Editor ist ein Index in eine Liste mit färbbare Elemente. Jede färbbare Element gibt einen Farbwert und einen Satz von Schriftartattributen, z. B. fett oder durchgestrichen. Der Editor stellt einen Satz von färbbare Standardelemente, die Ihre Sprachdienst verwenden können. Alles, was Sie tun müssen ist, geben Sie die entsprechende Farbe Index für jeden Typ des Sicherheitstokens. Sie können allerdings stellen eine Reihe von benutzerdefinierte färbbare Elemente und die Indizes, die Sie angeben, für die Token und verweisen auf einer eigenen Liste von färbbare Elemente statt der Standardliste. Müssen Sie auch Festlegen der `RequestStockColors` Registrierungseintrag auf 0 (oder geben Sie keine der `RequestStockColors` Eintrag überhaupt) zur Unterstützung benutzerdefinierter Farben. Einstellbaren dieses Registrierungseintrags durch einen benannten Parameter, um die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> benutzerdefiniertes Attribut. Weitere Informationen zu registrieren einen Sprachdienst und seine Optionen festlegen, finden Sie unter [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Benutzerdefinierte Färbbare Elemente  
 Um eine eigene benutzerdefinierte färbbare Elemente angeben möchten, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> und <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Die erste Methode gibt die Anzahl der benutzerdefinierte färbbare Elemente, die Ihre Sprachdienst unterstützt, und die zweite das benutzerdefinierte färbbare Element anhand des Indexes ab. Sie erstellen die Standardliste der benutzerdefinierte färbbare Elemente. Im Konstruktor des Language-Diensts wird alles, was Sie tun müssen ist Geben Sie jedes färbbare Element mit einem Namen. Visual Studio behandelt automatisch die Groß-/Kleinschreibung, in denen der Benutzer einen anderen Satz von färbbare Elemente auswählt. Dieser Name wird in der **Schriftarten und Farben** Eigenschaftenseite auf die **Optionen** (Dialogfeld) (in Visual Studio verfügbar **Tools** Menü) und dieser Name wird bestimmt, welche die Farbe eines Benutzers wurde außer Kraft. Auswahl des Benutzers werden in einem Cache in der Registrierung gespeichert und den Namen zugreifen. Die **Schriftarten und Farben** Eigenschaftenseite zeigt eine Liste aller Farbnamen in alphabetischer Reihenfolge, deshalb Sie benutzerdefinierten Farben gruppieren können, jede Farbnamen durch den Namen Ihres Language; abgrenzen, indem Sie z. B. "**TestLanguage - Kommentar**"und"**TestLanguage - Schlüsselwort**". Oder Sie können Ihre färbbare Elemente nach dem Regeltyp gruppieren "**Kommentar (TestLanguage)**"und"**Schlüsselwort (TestLanguage)**". Gruppierung nach Sprachenname wird bevorzugt.  
  
> [!CAUTION]
>  Es wird dringend empfohlen, dass Sie der Name der Sprache im Namen färbbare Element zum Vermeiden von Konflikten mit vorhandenen Namen von färbbare Element einschließen.  
  
> [!NOTE]
>  Wenn Sie während der Entwicklung der Name eines der Farben ändern, müssen Sie den Cache zurücksetzen, den Visual Studio erstellt beim ersten Farben auf die zugegriffen wurde. Können Sie dies tun, durch Ausführen der **Zurücksetzen der experimentellen Struktur** Befehl aus der Visual Studio SDK.  
  
 Beachten Sie, dass das erste Element in der Liste der färbbare Elemente nie darauf verwiesen wird. Visual Studio stellt immer die Standardfarben für Text und die Attribute für dieses Element. Die einfachste Möglichkeit für den Umgang mit diesem ist ein Platzhalter färbbare Element als erstes Element angeben.  
  
### <a name="high-color-colorable-items"></a>Färbbare High Color-Elemente  
 Färbbare Elemente können außerdem 24-Bit- oder hohe Farbwerte über unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle. Das MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> -Klasse unterstützt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Schnittstelle und die 24-Bit-Farben im Konstruktor zusammen mit der normalen Farben angegeben werden. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.ColorableItem>-Klasse. Das folgende Beispiel zeigt, wie die 24-Bit-Farben für Schlüsselwörter und Kommentare. Die 24-Bit-Farben werden verwendet, wenn 24-Bit-Farbe auf dem Desktop des Benutzers unterstützt wird. Andernfalls werden die normalen Textfarben verwendet.  
  
 Beachten Sie, dass dies die Standardfarben für Ihre Sprache sind; der Benutzer kann diese Farben ändern, um alle von Ihnen gewünschten werden soll.  
  
### <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Möglichkeit zum Deklarieren und füllen Sie ein Array von benutzerdefinierte färbbare Elemente, die mithilfe der <xref:Microsoft.VisualStudio.Package.ColorableItem> Klasse. In diesem Beispiel wird das Schlüsselwort und einen Kommentar Farben mit 24-Bit-Farben an.  
  
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
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>Die Colorizer-Klasse und der Scanner  
 Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse verfügt über eine <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> Methode, Instantiantes der <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse. Der Scanner, die von zurückgegeben wird die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> wird die Methode zum Übergeben der <xref:Microsoft.VisualStudio.Package.Colorizer> Klassenkonstruktor.  
  
 Sie implementieren müssen die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode in eine eigene Version der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse anhand den Scanner alle token Farbinformationen abzurufen.  
  
 Der Scanner muss zum Auffüllen einer <xref:Microsoft.VisualStudio.Package.TokenInfo> -Struktur für jedes Token es findet. Diese Struktur enthält Informationen, wie z. B. die Spanne der Token, belegt den Farbe Index zu verwenden, welcher die token und token-Trigger ist (finden Sie unter <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Nur der Index Spanne und Farbe für die farbliche Kennzeichnung von erforderlich sind die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse.  
  
 Der Color-Index gespeichert wird, der <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur ist in der Regel einen Wert aus der <xref:Microsoft.VisualStudio.Package.TokenColor> -Enumeration, die eine Reihe von benannten Indizes, die für verschiedene Sprachelemente wie Schlüsselwörtern und Operatoren enthält. Wenn Ihre benutzerdefinierte färbbare Elemente Übereinstimmungen Auflisten der Elemente angezeigt, der <xref:Microsoft.VisualStudio.Package.TokenColor> -Enumeration, dann können nur verwenden Sie die Enumeration als Farbe für jedes Token. Allerdings können, wenn Sie zusätzliche färbbare Elemente haben oder nicht vorhandene Werte in dieser Reihenfolge verwenden möchten, Sie anordnen Ihre benutzerdefinierte färbbare Elementliste um Ihren Anforderungen entsprechen und den entsprechenden Index in der Liste zurückgegeben. Seien Sie sicher, dass den Index umgewandelt eine <xref:Microsoft.VisualStudio.Package.TokenColor> in zum Speichern der <xref:Microsoft.VisualStudio.Package.TokenInfo> -Struktur sind. [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] sieht nur den Index.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie der Scanner drei Tokentypen identifizieren möglicherweise: Zahlen, Satzzeichen und Bezeichner (Elemente, die keine Zahl oder Interpunktionszeichen). In diesem Beispiel wird nur zu Illustrationszwecken und stellt eine umfassende Parser und Scanner Implementierung keine dar. Es wird davon ausgegangen, dass es ist ein `Lexer` -Klasse mit einer `GetNextToken()` Methode, die eine Zeichenfolge zurückgibt.  
  
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
 [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

---
title: Syntax-Farbbeimbereitung in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704707"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Einfärben der Syntax in einem Legacysprachdienst
Syntax-Farbgebung ist ein Feature, das bewirkt, dass verschiedene Elemente einer Programmiersprache in einer Quelldatei in verschiedenen Farben und Stilen angezeigt werden. Um diese Funktion zu unterstützen, müssen Sie einen Parser oder Scanner bereitstellen, der die Typen von lexikalischen Elementen oder Token in der Datei identifizieren kann. Viele Sprachen unterscheiden Schlüsselwörter, Trennzeichen (z. B. Klammern oder Geschweifungen) und Kommentare, indem sie sie auf unterschiedliche Weise kolorieren.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="implementation"></a>Implementierung
 Um die Farbgebung zu unterstützen, enthält <xref:Microsoft.VisualStudio.Package.Colorizer> das Verwaltete Paketframework (MPF) die Klasse, die die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle implementiert. Diese Klasse interagiert mit einem, <xref:Microsoft.VisualStudio.Package.IScanner> um das Token und die Farben zu bestimmen. Weitere Informationen zu Scannern finden Sie unter [Legacy Language Service Parser and Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse markiert dann jedes Zeichen des Tokens mit den Farbinformationen und gibt diese Informationen an den Editor zurück, der die Quelldatei anzeigt.

 Die an den Editor zurückgegebenen Farbinformationen sind ein Index in einer Liste von befärbbaren Elementen. Jedes farbliche Element gibt einen Farbwert und eine Reihe von Schriftartattributen an, z. B. Fett oder durchgestrichen. Der Editor stellt eine Reihe von standardmäßigen farbbaren Elementen zur Verfügung, die Ihr Sprachdienst verwenden kann. Sie müssen lediglich den entsprechenden Farbindex für jeden Tokentyp angeben. Sie können jedoch eine Reihe benutzerdefinierter befärbbarer Elemente und der Indizes bereitstellen, die Sie für Token bereitstellen, und anstelle der Standardliste auf Ihre eigene Liste von befärbten Elementen verweisen. Sie müssen auch `RequestStockColors` den Registrierungseintrag auf 0 `RequestStockColors` festlegen (oder den Eintrag überhaupt nicht angeben), um benutzerdefinierte Farben zu unterstützen. Sie können diesen Registrierungseintrag mit einem <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> benannten Parameter auf das benutzerdefinierte Attribut festlegen. Weitere Informationen zum Registrieren eines Sprachdienstes und zum Festlegen seiner Optionen finden Sie unter [Registrieren eines Legacy-Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Benutzerdefinierte einfärbbare Elemente
 Um eigene benutzerdefinierte befärbbare Elemente <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> anzugeben, müssen Sie die and-Methode <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse überschreiben. Die erste Methode gibt die Anzahl der benutzerdefinierten befärbbaren Elemente zurück, die von Ihrem Sprachdienst unterstützt werden, und die zweite methode ruft das benutzerdefinierte befärbbare Element nach Index ab. Sie erstellen die Standardliste der benutzerdefinierten befärbbaren Elemente. Im Konstruktor Ihres Sprachdienstes müssen Sie nur jedes befärbbare Element mit einem Namen versorgen. Visual Studio behandelt automatisch den Fall, in dem der Benutzer einen anderen Satz von befärbten Elementen auswählt. Dieser Name wird auf der Eigenschaftenseite **"Schriftarten und Farben"** im Dialogfeld **Optionen** (verfügbar im Menü "Visual Studio **Tools")** angezeigt, und dieser Name bestimmt, welche Farbe ein Benutzer überschrieben hat. Die Auswahlmöglichkeiten des Benutzers werden in einem Cache in der Registrierung gespeichert und über den Farbnamen zugegriffen. Auf der Eigenschaftenseite **Schriftarten und Farben** werden alle Farbnamen in alphabetischer Reihenfolge aufgelistet, sodass Sie Ihre benutzerdefinierten Farben gruppieren können, indem Sie jedem Farbnamen ihren Sprachnamen voranstellen. z. B. "**TestLanguage- Comment**" und "**TestLanguage- Keyword**". Sie können auch Ihre farblichen Elemente nach Typ "**Kommentar (TestLanguage)**" und "**Keyword (TestLanguage)**" gruppieren. Die Gruppierung nach Sprachnamen wird bevorzugt.

> [!CAUTION]
> Es wird dringend empfohlen, den Sprachnamen in den befärbbaren Elementnamen aufzunehmen, um Kollisionen mit vorhandenen befärbbaren Elementnamen zu vermeiden.

> [!NOTE]
> Wenn Sie den Namen einer Ihrer Farben während der Entwicklung ändern, müssen Sie den Cache zurücksetzen, den Visual Studio beim ersten Zugriff auf Ihre Farben erstellt hat. Sie können dies tun, indem Sie den Befehl **"Experimentelle Hive zurücksetzen"** aus dem Programmmenü des Visual Studio SDK ausführen.

 Beachten Sie, dass auf das erste Element in der Liste der befärbten Elemente nie verwiesen wird. Visual Studio stellt immer die Standardtextfarben und -attribute für dieses Element zur Verfügung. Der einfachste Weg, damit umzugehen, ist die Angabe eines Platzhalters, der als erstes Element einbeiniges Element liefert.

### <a name="high-color-colorable-items"></a>Hochfarblich befärbbare Artikel
 Befärbbare Elemente können auch 24-Bit- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> oder hohe Farbwerte über die Schnittstelle unterstützen. Die <xref:Microsoft.VisualStudio.Package.ColorableItem> MPF-Klasse <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> unterstützt die Schnittstelle, und die 24-Bit-Farben werden im Konstruktor zusammen mit den normalen Farben angegeben. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.ColorableItem>-Klasse. Das folgende Beispiel zeigt, wie Sie die 24-Bit-Farben für Schlüsselwörter und Kommentare festlegen. Die 24-Bit-Farben werden verwendet, wenn 24-Bit-Farben auf dem Desktop des Benutzers unterstützt werden. Andernfalls werden die normalen Textfarben verwendet.

 Denken Sie daran, dies sind die Standardfarben für Ihre Sprache; Der Benutzer kann diese Farben in das ändern, was er möchte.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine Möglichkeit zum Deklarieren und Auffüllen <xref:Microsoft.VisualStudio.Package.ColorableItem> eines Arrays benutzerdefinierter befärbbarer Elemente mithilfe der Klasse. In diesem Beispiel werden die Schlüsselwort- und Kommentarfarben mithilfe von 24-Bit-Farben festgelegt.

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
 Die <xref:Microsoft.VisualStudio.Package.LanguageService> Basisklasse <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> verfügt über eine Methode, die die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse instanziiert. Der von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode zurückgegebene Scanner <xref:Microsoft.VisualStudio.Package.Colorizer> wird an den Klassenkonstruktor übergeben.

 Sie müssen <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> die Methode in Ihrer <xref:Microsoft.VisualStudio.Package.LanguageService> eigenen Version der Klasse implementieren. Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse verwendet den Scanner, um alle Tokenfarbinformationen abzurufen.

 Der Scanner muss für <xref:Microsoft.VisualStudio.Package.TokenInfo> jedes gefundene Token eine Struktur auffüllen. Diese Struktur enthält Informationen wie die Spanne, die das Token belegt, den zu verwendenden <xref:Microsoft.VisualStudio.Package.TokenTriggers>Farbindex, den Typ des Tokens und Tokentrigger (siehe ). Nur die Spanne und der Farbindex <xref:Microsoft.VisualStudio.Package.Colorizer> werden für die Farbgebung durch die Klasse benötigt.

 Der in der <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur gespeicherte Farbindex <xref:Microsoft.VisualStudio.Package.TokenColor> ist in der Regel ein Wert aus der Enumeration, der eine Reihe benannter Indizes bereitstellt, die verschiedenen Sprachelementen wie Schlüsselwörtern und Operatoren entsprechen. Wenn Ihre benutzerdefinierte liste farbbare Elemente <xref:Microsoft.VisualStudio.Package.TokenColor> mit den in der Enumeration dargestellten Elementen übereinstimmt, können Sie einfach die Enumeration als Farbe für jedes Token verwenden. Wenn Sie jedoch über zusätzliche befärbbare Elemente verfügen oder die vorhandenen Werte in dieser Reihenfolge nicht verwenden möchten, können Sie die liste für benutzerdefinierte befärbbare Elemente an Ihre Anforderungen anpassen und den entsprechenden Index in diese Liste zurücksenden. Achten Sie einfach darauf, <xref:Microsoft.VisualStudio.Package.TokenColor> den Index in <xref:Microsoft.VisualStudio.Package.TokenInfo> eine zu werfen, wenn Sie ihn in der Struktur speichern; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] sieht nur den Index.

### <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie der Scanner drei Tokentypen identifizieren kann: Zahlen, Satzzeichen und Bezeichner (alles, was keine Zahl oder Interpunktion ist). Dieses Beispiel dient nur zur Veranschaulichung und stellt keine umfassende Parser- und Scannerimplementierung dar. Es wird davon `Lexer` ausgegangen, `GetNextToken()` dass es eine Klasse mit einer Methode gibt, die eine Zeichenfolge zurückgibt.

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

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

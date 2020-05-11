---
title: Gliederung in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706809"
---
# <a name="outlining-in-a-legacy-language-service"></a>Gliederung in einem Legacysprachdienst
Die Gliederung ermöglicht es, ein komplexes Programm in eine Übersicht oder Gliederung zu reduzieren. Beispielsweise können z. B. alle Methoden in einer einzigen Zeile reduziert werden, in der nur die Methodensignatur angezeigt wird. Darüber hinaus können Strukturen und Klassen reduziert werden, um nur die Namen der Strukturen und Klassen anzuzeigen. Innerhalb einer einzigen Methode kann eine komplexe Logik reduziert werden, um den Gesamtfluss anzuzeigen, indem nur die erste Zeile von Anweisungen wie , `foreach` `if`und `while`angezeigt wird.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Walkthrough: Umreißen](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="enabling-support-for-outlining"></a>Aktivieren der Unterstützung für Dieginierung
 Der `AutoOutlining` Registrierungseintrag ist auf 1 festgelegt, um die automatische Gliederung zu aktivieren. Die automatische Gliederung richtet eine Analyse der gesamten Quelle ein, wenn eine Datei geladen oder geändert wird, um ausgeblendete Bereiche zu identifizieren und die Gliederungsglyphen anzuzeigen. Die Gliederung kann auch manuell vom Benutzer gesteuert werden.

 Der Wert `AutoOutlining` des Registrierungseintrags kann <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> über <xref:Microsoft.VisualStudio.Package.LanguagePreferences> die Eigenschaft in der Klasse abgerufen werden. Der `AutoOutlining` Registrierungseintrag kann mit einem benannten <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Parameter für das Attribut initialisiert werden (Details finden Sie unter [Registrieren eines Legacy-Sprachdienstes).](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="the-hidden-region"></a>Die verborgene Region
 Um eine Gliederung zu ermöglichen, muss Ihr Sprachdienst ausgeblendete Bereiche unterstützen. Dies sind Textspannen, die erweitert oder reduziert werden können. Ausgeblendete Bereiche können durch Standardsprachensymbole, z. B. geschweifte Klammern, oder durch benutzerdefinierte Symbole getrennt werden. Beispielsweise verfügt das Unternehmen `#region` / `#endregion` über ein Paar, das einen ausgeblendeten Bereich abgrenzt.

 Ausgeblendete Bereiche werden von einem ausgeblendeten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Regions-Manager verwaltet, der als Schnittstelle verfügbar gemacht wird.

 Die Gliederung <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> verwendet ausgeblendete Bereiche der Schnittstelle und enthält die Spanne des ausgeblendeten Bereichs, den aktuellen sichtbaren Zustand und das Banner, das angezeigt werden soll, wenn die Spanne reduziert wird.

 Der Sprachdienstparser <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> verwendet die Methode, um einen neuen ausgeblendeten <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Bereich mit dem Standardverhalten für ausgeblendete Bereiche hinzuzufügen, während die Methode es Ihnen ermöglicht, die Darstellung und das Verhalten der Gliederung anzupassen. Sobald ausgeblendete Bereiche der ausgeblendeten Regionssitzung übergeben wurden, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden die ausgeblendeten Bereiche für den Sprachdienst verwaltet.

 Wenn Sie bestimmen müssen, wann die Sitzung für den ausgeblendeten Bereich zerstört wird, wird ein ausgeblendeter Bereich geändert, oder Sie müssen sicherstellen, dass ein bestimmter ausgeblendeter Bereich sichtbar ist. Sie müssen eine Klasse <xref:Microsoft.VisualStudio.Package.Source> von der Klasse ableiten <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>und <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>die entsprechenden Methoden , und , bzw. überschreiben.

### <a name="example"></a>Beispiel
 Hier ist ein vereinfachtes Beispiel für das Erstellen ausgeblendeter Bereiche für alle Paare von geschweiften Klammern. Es wird davon ausgegangen, dass die Sprache einen Kordbundabgleich bereitstellt und dass die zu gleichen Klammern mindestens die geschweiften Geschwenen enthalten. Dieser Ansatz dient nur zur Veranschaulichung. Eine vollständige Umsetzung hätte eine vollständige <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Bearbeitung der Fälle in . In diesem Beispiel wird <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> auch `true` gezeigt, wie die Voreinstellung vorübergehend festgelegt wird. Eine Alternative besteht `AutoOutlining` darin, den `ProvideLanguageServiceAttribute` benannten Parameter im Attribut in Ihrem Sprachpaket anzugeben.

 In diesem Beispiel werden die Regeln für Kommentare, Zeichenfolgen und Literale von C-Regeln angenommen.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

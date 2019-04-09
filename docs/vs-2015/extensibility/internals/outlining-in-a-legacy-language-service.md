---
title: Gliederung in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c99943a2f0ebd05236caf7706021cfb8ac58fa84
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957152"
---
# <a name="outlining-in-a-legacy-language-service"></a>Gliederung in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gliederung ermöglicht es, ein komplexes Programm in einer Übersicht bzw. die Gliederung zu reduzieren. In C# können z. B. alle Methoden einer einzelnen Zeile zeigt nur die Signatur der Methode reduziert werden. Darüber hinaus können Strukturen und Klassen reduziert werden, um nur die Namen der Strukturen und Klassen angezeigt. In einer einzelnen Methode, komplexer Logik reduziert werden kann, um den Gesamtablauf anzeigen, indem Sie nur die erste Zeile von Anweisungen wie z. B. mit `foreach`, `if`, und `while`.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Exemplarische Vorgehensweise: Gliedern](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="enabling-support-for-outlining"></a>Aktivieren der Unterstützung für eine Gliederung  
 Die `AutoOutlining` Registrierungseintrags auf 1 festgelegt ist, um automatische Gliederung zu aktivieren. Automatische Gliederung richtet eine Analyse der gesamten Quelle, wenn eine Datei geladen oder geändert, um die ausgeblendeten Bereiche zu identifizieren und die Gliederung Symbole anzeigen. Gliederung kann auch manuell vom Benutzer gesteuert werden.  
  
 Der Wert des der `AutoOutlining` Eintrag in der Registrierung erhalten Sie über die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Eigenschaft für die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Die `AutoOutlining` Registrierungseintrag kann initialisiert werden, mit einem benannten Parameter, um die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attribut (finden Sie unter [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md) Einzelheiten).  
  
## <a name="the-hidden-region"></a>Der ausgeblendete Bereich  
 Um Gliederung zu gewährleisten, muss der Sprachdienst ausgeblendeten Bereiche unterstützen. Hierbei handelt es sich um Spannen der Text, der erweitert oder reduziert werden können. Ausgeblendete Bereiche können Standardsprache-Symbole, z. B. von geschweiften Klammern oder durch benutzerdefinierte Symbole getrennt werden. Z. B. C# verfügt über eine `#region` / `#endregion` -Paar, das einen ausgeblendeten Bereich begrenzt.  
  
 Ausgeblendete Bereiche werden durch einen Manager für ausgeblendete Bereiche, die als verfügbar gemacht wird verwaltet die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> Schnittstelle.  
  
 Gliedern von ausgeblendeten Bereichen verwendet die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> -Schnittstelle und enthalten die Spanne des ausgeblendeten Bereichs, der derzeit sichtbaren Zustand und das Banner angezeigt werden, wenn die Spanne reduziert ist.  
  
 Die sprachdienstparser verwendet die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Methode, um einen neuen ausgeblendeten Bereich mit dem Standardverhalten für ausgeblendete Bereiche hinzuzufügen während der <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> Methode können Sie das Aussehen und Verhalten der Gliederung anpassen. Nach der ausgeblendeten Bereiche, die der Sitzung des ausgeblendeten Bereichs, erteilt werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] der ausgeblendeten Bereiche für den Sprachdienst verwaltet.  
  
 Bei Bedarf, um zu bestimmen, wenn die Sitzung des ausgeblendeten Bereich zerstört wird, ein ausgeblendeter Bereich geändert wird, oder Sie müssen Sie sicherstellen, dass ein bestimmter verborgener Bereich angezeigt wird; Sie müssen leiten eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> Klasse, und überschreiben Sie die entsprechenden Methoden, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, und <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>bzw.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel der Erstellung der ausgeblendeten Bereiche für alle Paare von geschweiften Klammern ein. Es wird davon ausgegangen, dass die Sprache bereitstellt, Zuordnung von geschweiften Klammern und geschweiften Klammern in geschweiften Klammern, um die abzugleichenden mindestens enthalten sein ({und}). Dieser Ansatz ist nur zur Veranschaulichung. Eine vollständige Implementierung hätte eine vollständige Behandlung der Fälle im <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Dieses Beispiel zeigt auch Gewusst wie: Festlegen der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Vorrang `true` vorübergehend. Geben Sie eine Alternative ist die `AutoOutlining` benannten Parameter in der `ProvideLanguageServiceAttribute` Attribut im Language-Paket.  
  
 In diesem Beispiel wird davon ausgegangen, C#-Regeln für Kommentare, Zeichenfolgen und Literale.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
